# 🧠 Fundamentos Técnicos: Cómo funciona Nexo

Este documento profundiza en la ingeniería detrás del **Asistente Personal Nexo (Open Gravity)**, explicando el funcionamiento interno de sus componentes core y sus recientes mejoras evolutivas.

---

## 🛰️ 1. Gateway Central: El Plano de Control
El Gateway es una aplicación Node.js/TypeScript que actúa como el "sistema nervioso central".
*   **Protocolo Híbrido**: Utiliza WebSockets (`ws`) para telemetría en tiempo real y comunicación bidireccional con los nodos, y un servidor HTTP para webhooks y APIs externas.
*   **Gestión de Presencia**: Mantiene un registro de "Heartbeast" de todos los nodos conectados.

## 🤖 2. Motor LLM e Inteligencia Adaptativa
Nexo no depende de un solo modelo. Su motor (`LLMEngine`) está diseñado para la resiliencia:
*   **Failover Algorítmico**: Intento primario con **Groq** (baja latencia) y respaldo automático con **OpenRouter**.
*   **Inyección Determinista de Herramientas**: El motor inyecta herramientas en el LLM con descripciones enriquecidas que fuerzan el uso de herramientas seguras (ej: prioriza MCP SQLite sobre comandos de terminal manuales).

## 🛡️ 3. Desktop Node: Ejecución Zero-Trust
El nodo es el "músculo" que vive en el hardware del usuario. 
*   **Handshake Certificado**: Intercambio de tokens asimétricos para establecer la confianza.
*   **Intercepción Determinista**: Bloqueo proactivo de comandos peligrosos (`sudo`, `rm`, etc.) mediante un motor de reglas previo a la ejecución.

## 🧩 4. Orquestación y Enrutamiento de Intenciones
Nexo utiliza un **Orquestador Heurístico** que decide qué especialista debe manejar cada tarea basándose en patrones de lenguaje natural y disponibilidad de nodos.

## 🔌 5. Extensión Segura via MCP (Model Context Protocol) - [MEJORADO v1.7.0]
MCP es la "Aduana Universal" de herramientas. Las mejoras de la Fase 9 incluyen:
*   **Instancias Efímeras (TTL)**: Los servidores MCP se activan bajo demanda y se auto-cierran tras 60s de inactividad, optimizando el consumo de RAM.
*   **Interceptor DLP (DLP Sanitizer)**: Capa de protección de datos que desinfecta los argumentos enviados a herramientas externas para evitar fugas de información sensible.
*   **Circuit Breaker**: Sistema de protección que aísla servidores MCP fallidos (ej. timeouts en Perplexity) para evitar la degradación del Gateway.
*   **Network Guard**: Aplicación de políticas de salida (Egress Policies) para restringir las conexiones de las extensiones.

## 👁️ 6. Sistema Sentinel 2.0: Vigilancia Vital - [MEJORADO v1.7.0]
Sentinel ha evolucionado de un simple monitor de logs a un administrador de salud proactivo:
*   **Motor de Reanimación (Auto-Heal)**: Si el Gateway falla en 3 chequeos consecutivos, Sentinel interviene: mata procesos huérfanos en el puerto 3000 y reinicia el sistema vía PM2 o arranque manual.
*   **Anti-Ofuscación Avanzada**: Normalización de texto que detecta ataques camuflados (ej. `s u d o`, `p.a.s.s.w.d`).
*   **Reporting VITAL**: Generación de informes de salud interactivos (`getSystemStatus`) con métricas de CPU, RAM y estado de todos los servicios PM2.
*   **Knowledge Base de Amenazas**: Traduce alertas técnicas a lenguaje humano para el usuario de Telegram.

---

## 📂 Estructura de Datos (Persistencia)
Nexo sigue una estructura estricta en el directorio raíz del usuario:
*   `~/.nexo/workspace/sessions/`: Cada chat es un JSON cronológico.
*   `~/.nexo/security/`: Almacenes de secretos, threat KB y listas blancas.
*   `~/.nexo/.nexo_data/nexo.db`: Base de datos SQLite para memoria estructurada.

---

> El desarrollo de Nexo se basa en la robustez: el sistema está diseñado para autoprotegerse y auto-repararse.
