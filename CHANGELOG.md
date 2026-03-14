# 📜 Changelog: Nexo

Todos los cambios notables en este proyecto serán documentados en este archivo.

## [1.7.0] - 2026-03-14 (Mejoras MCP & Sentinel 2.0)

### Sentinel 2.0 (Vigilancia Vital)
- **Añadido**: **Protocolo Auto-Heal**: Capacidad de reanimación automática del sistema tras 3 fallos de salud (reinicio vía PM2 o limpieza de puertos).
- **Añadido**: **Reporting VITAL**: Informes de salud en tiempo real (`getSystemStatus`) con métricas de hardware y servicios.
-  **Mejorado**: **Anti-Ofuscación**: Motor de normalización que detecta comandos camuflados (ej. `s.u.d.o`, `r o o t`) eliminando ruidos y colapsando espaciados.
- **Añadido**: **Threat Knowledge Base**: Base de datos de amenazas con traducciones humanas y estrategias de defensa sugeridas.

### MCP Extensions (Habilidades Seguras)
- **Añadido**: **Instancias Efímeras (TTL)**: Servidores MCP en modo "on-demand" que se cierran tras 60s de inactividad para optimizar RAM.
- **Añadido**: **Interceptor DLP (Data Loss Prevention)**: Filtrado sanitario de inputs antes de enviar datos a herramientas externas.
- **Añadido**: **Network Guard Egress**: Políticas de filtrado de red para las capas de extensión.
- **Mejorado**: **Inyección Determinista**: Inyección inteligente de herramientas en el LLM con descripciones de prioridad (Force SQLite usage).

---

## [1.6.0] - 2026-03-14 (Fase 9 - MCP Secure Integration)
- **Añadido**: Secure MCP Client para consumo de herramientas externas.
- **Añadido**: Aduana de herramientas via `mcp_allowlist.json`.
- **Mejorado**: Circuit Breaker para servidores MCP.

## [1.5.0] - 2026-03-14 (Fase 8 - Sentinel Monitoring)
- **Añadido**: Sistema Sentinel para monitorización pasiva de logs.
- **Añadido**: Alertas en Telegram ante intentos de intrusión.
- **Añadido**: Threat Knowledge Base local.

## [1.4.5] - 2026-03-14 (Fase 7 - Agente de Calidad Determinista)
- **Añadido**: Deterministic Security Auditor: Chequeo nativo de permisos y integridad de secretos (.env).
- **Añadido**: Functional Auditor: Monitorización de puertos vitales (Port 3000) y métricas de RAM/Heap.
- **Añadido**: Intelligent Diagnostics: Activación del LLM solo ante fallos detectados.
- **Añadido**: QALogger: Persistencia estructurada de auditorías.

## [1.4.0] - 2026-03-14 (Fase 6 - Zero Trust Desktop Node)
- **Añadido**: Desktop Node desacoplado con handshake certificado.
- **Añadido**: Intercepción de comandos prohibidos.
- **Añadido**: Auditoría forense en `logs/node-audit.log`.
