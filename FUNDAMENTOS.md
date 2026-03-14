# 🧠 Fundamentos Técnicos: Cómo funciona Nexo

Este documento profundiza en la ingeniería detrás del **Asistente Personal Nexo (Open Gravity)**, explicando el funcionamiento interno de sus componentes core.

---

## 🛰️ 1. Gateway Central: El Plano de Control
El Gateway es una aplicación Node.js/TypeScript que actúa como el "sistema nervioso central".
*   **Protocolo Híbrido**: Utiliza WebSockets (`ws`) para telemetría en tiempo real y comunicación bidireccional con los nodos, y un servidor HTTP para webhooks y APIs externas.
*   **Gestión de Presencia**: Mantiene un registro de "Heartbeast" de todos los nodos conectados (Desktop, Mobile, etc.). Si un nodo se desconecta, Nexo lo sabe al instante y redirige las tareas.

## 🤖 2. Motor LLM e Inteligencia Adaptativa
Nexo no depende de un solo modelo. Su motor (`LLMEngine`) está diseñado para la resiliencia:
*   **Failover Algorítmico**: 
    1.  Intenta la petición con **Groq** (Llama-3 o similar) por su baja latencia (<500ms).
    2.  Si detecta un Error 429 (Rate Limit), 503 (Overloaded) o un Timeout, captura la excepción.
    3.  Automáticamente re-empaqueta el contexto y lanza la misma petición a **OpenRouter** como respaldo.
*   **System Prompt Dinámico**: Inyecta dinámicamente la lista de herramientas disponibles según el nodo que esté conectado en ese momento.

## 🛡️ 3. Desktop Node: Ejecución Zero-Trust
El nodo es el "músculo" que vive en el hardware del usuario. 
*   **Handshake Certificado**: Al iniciar, el nodo intercambia un token secreto con el Gateway para establecer un túnel cifrado.
*   **Intercepción Determinista**: Antes de que el comando de terminal (ej. `ls -la`) toque el sistema operativo, pasa por una función de filtrado:
    ```typescript
    if (command.includes('sudo') || command.includes('rm -rf')) {
        throw new Error("Comando bloqueado por política de seguridad");
    }
    ```
*   **Aislamiento**: El nodo puede estar en una red física diferente al Gateway (conectados vía Tailscale), proporcionando una capa física de separación.

## 🧩 4. Orquestación y Enrutamiento de Intenciones
Nexo utiliza un **Orquestador Heurístico** que decide qué especialista debe manejar cada tarea:
1.  **Clasificador**: Analiza el texto del usuario buscando patrones (ej. "busca en la web" -> Especialista Browser).
2.  **Dispatcher**: Envía la carga de trabajo (payload) al socket específico del agente especializado.
3.  **Circuit Breaker**: Si un especialista falla repetidamente, el Orquestador lo marca como "fuera de servicio" para evitar que el sistema se degrade.

## 🔌 5. Integración MCP (Model Context Protocol)
MCP es la "Aduana Universal" de herramientas. 
*   **Stdio Transport**: Nexo lanza procesos hijos que hablan el protocolo MCP.
*   **Middleware de Seguridad**: Entre el LLM y el servidor MCP, existe una capa de validación que comprueba si la operación solicitada está permitida para ese servidor específico en la `mcp_allowlist.json`.

## 👁️ 6. Sistema Sentinel: Seguridad Pasiva 24/7
A diferencia de los guardias tradicionales que bloquean puertas, Sentinel **vigila las cámaras (logs)**.
*   **Watcher**: Observa los cambios en el sistema de archivos de logs.
*   **Regex Engine**: Busca secuencias sospechosas que intentan engañar a los filtros básicos (ej: `cat /etc/p"as"swd`).
*   **Notificador**: Ante una coincidencia, interrumpe el flujo normal y envía un reporte forense al usuario por Telegram.

---

## 📂 Estructura de Datos (Persistencia)
Nexo sigue una estructura estricta en el directorio raíz del usuario:
*   `~/.nexo/workspace/sessions/`: Cada chat es un JSON cronológico.
*   `~/.nexo/security/`: Almacenes de secretos y listas blancas.
*   `~/.nexo/.nexo_data/nexo.db`: Base de datos SQLite para memoria estructurada (eventos, usuarios, métricas).

---

> El desarrollo de Nexo se basa en la modularidad: cada pieza puede ser reemplazada o mejorada sin afectar al resto de la infraestructura.
