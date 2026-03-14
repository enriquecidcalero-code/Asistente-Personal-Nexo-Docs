# 📜 Changelog: Nexo

Todos los cambios notables en este proyecto serán documentados en este archivo.

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

## [1.3.0] - 2026-03-14 (Fase 5)
- **Añadido**: Motor proactivo (CRON) para tareas programadas.
- **Añadido**: Live Canvas (A2UI) con validación Zod.
- **Añadido**: Superficie de Webhooks HTTP.

## [1.2.0] - 2026-03-13 (Fase 4 - Audio & Memoria)
- **Añadido**: Multi-Agent Orchestration y control de recursividad.
- **Añadido**: Dynamic Skills Registry.
- **Añadido**: ElevenLabs TTS integration.

## [1.1.5] - 2026-03-13 (Fase 3 - Gateway CORE & Cloud Security)
- **Añadido**: Central Control Plane: Orquestador WebSocket para eventos y sesiones.
- **Añadido**: Tailscale Network Guard: Bloqueo automático si no hay anclaje seguro a 127.0.0.1.
- **Añadido**: Session Dispatcher y Presence Engine.

## [1.1.0] - 2026-03-13 (Fase 2)
- **Añadido**: Nodos locales con `system.run` y `system.notify`.
- **Añadido**: Control de navegador (CDP) via `NexoBrowser`.
- **Añadido**: Módulo `NexoSecurity` integrado.

## [1.0.0] - 2026-03-13 (Fase 1)
- **Añadido**: Gateway WebSocket base.
- **Añadido**: Integración con Groq y OpenRouter con Failover.
- **Añadido**: Canal de Telegram con DM Pairing.
