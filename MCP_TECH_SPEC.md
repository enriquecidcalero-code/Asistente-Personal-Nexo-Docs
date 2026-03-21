# Especificación Técnica: Arquitectura MCP en Nexo (Open Gravity)

## 1. Topología del Sistema
Nexo implementa el **Model Context Protocol (MCP v1.0)** como su plano de control (Control Plane) de extensibilidad. La topología es de tipo **Hub-and-Spoke**, donde el Gateway central actúa como el cliente primario orquestando múltiples servidores especializados.

## 2. Capa de Transporte y Mensajería
*   **Stdio (Standard I/O Transport)**: Nexo utiliza procesos hijos (Child Processes) aislados para cada servidor MCP. Las ráfagas de comunicación se realizan mediante **JSON-RPC 2.0** delimitado por líneas (`Line-Delimited JSON`).
*   **SSE (Server-Sent Events Transport)**: Preparado para la comunicación con servidores remotos/nube, permitiendo flujos de datos asíncronos y eventos de servidor (Server-Initiated Events).

## 3. Orquestación y Ciclo de Vida (Lifecycle)
*   **Instancias Efímeras (Ephemeral Mode)**: Para optimizar la huella de memoria (RAM footprint), Nexo implementa un recolector de basura (TTL Collector). Los servidores se instancian bajo demanda y se hibernan tras un periodo de inactividad ajustable (default: 60s).
*   **Circuit Breaker (Patrón de Estabilidad)**: Cada cliente MCP está envuelto en un disyuntor lógico que monitoriza la latencia y los códigos de error. Si un servidor alcanza el umbral de errores críticos, el sistema lo aísla (Open State) para proteger la estabilidad del núcleo del Gateway.

## 4. Seguridad y Validación (Aduana Digital)
*   **Aduana de Herramientas**: Implementación de un contrato de autorización binaria mediante `mcp_allowlist.json`. Ninguna llamada a `callTool` procede sin la validación previa contra la firma del servidor autorizado.
*   **DLP Sanitizer (Data Loss Prevention)**: Interceptor de capa media (Middleware) que escanea los argumentos de las herramientas buscando patrones sensibles (secrets, paths de sistema) antes de la serialización hacia transportes externos.
*   **Zod Schema Enforcement**: Todas las interfaces de entrada y salida son validadas contra esquemas Zod rigurosos para prevenir ataques de inyección de parámetros.

## 5. Integración con el Motor de Razonamiento (LLM)
Nexo realiza una **Inyección Determinista de Herramientas**. Transforma los esquemas JSON de MCP en definiciones de funciones OpenAI compatibles, enriqueciendo las descripciones para guiar la proactividad del modelo (ej: priorizando transacciones SQLite sobre comandos de terminal).

---
*Documentación Técnica de Ingeniería - Nexo Core Team*
