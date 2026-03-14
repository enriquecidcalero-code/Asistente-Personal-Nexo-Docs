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

## [1.1.0] - 2026-03-13 (Fase 2)
- **Añadido**: Nodos locales con `system.run` y `system.notify`.
- **Añadido**: Control de navegador (CDP) via `NexoBrowser`.
- **Añadido**: Módulo `NexoSecurity` integrado.

## [1.0.0] - 2026-03-13 (Fase 1)
- **Añadido**: Gateway WebSocket base.
- **Añadido**: Integración con Groq y OpenRouter con Failover.
- **Añadido**: Canal de Telegram con DM Pairing.
