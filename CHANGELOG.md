## [2.9.0] - 2026-04-06 (Fase 25 - Bibliotecario: Cerebro Digital & Obsidian RAG)

### Añadido
- **Fase 25: Bibliotecario & Obsidian RAG**: Implementación de navegación jerárquica en el Vault de Obsidian y sistema de lectura progresiva (L0-L2) para optimización de tokens.
- **Fase 24: Nexo DocOps**: Automatización de la documentación técnica con `doc-generator.ts` y registro ADR estructurado para trazabilidad total.
- **Fase 23: Memoria Semántica**: Integración de `sqlite-vss` para búsqueda vectorial local (Cortex Vectorial) garantizando privacidad Zero-Trust.
- **Fase 22: El Infiltrado**: Módulo de automatización de navegador con Playwright para interactuar con servicios sin API pública.
- **Fase 21: Resilience & Auto-Bootstrap**: Sistema de autocuración para infraestructura Docker (OrbStack) y Cortex Vectorial.

## [2.2.0] - 2026-03-31 (Fase 20 - Phalanx: Agente Blue Team y Defensa Activa)

### Añadido
- **Agente Phalanx (SOC Lead)**: Especialista en ciberseguridad defensiva, respuesta ante incidentes y análisis forense digital.
- **Escudo Determinista (IPS Engine)**: Motor de prevención de intrusiones en tiempo real con `LogTailer`, `Rate-limiting` y `Signature Matching`.
- **Integración Nativa con Firewall pf**: Automatización del bloqueo de IPs maliciosas mediante la inyección directa de reglas en el firewall de macOS (`pfctl`).
- **Analista Forense SOC (IA)**: Clasificación inteligente de vectores de ataque y generación de reportes forenses estructurados en JSON.
- **Protocolo de Juegos de Guerra (Wargames)**: Entorno controlado de simulación (Specter vs Phalanx) para la validación de la eficacia de las defensas.

## [2.1.5] - 2026-03-22 (Fase 19 - Specter: Intrusión & Red Team)

### Añadido
- **Agente Specter (Offensive Expert)**: Auditor ofensivo local dedicado a la detección proactiva de vulnerabilidades y validación de seguridad (Pentesting).
- **VulnerabilityScanner Determinista**: Herramientas integradas para ejecución de `Nmap`, auditoría de permisos de archivos sensibles (`stat`) y mapeo de superficie de ataque Docker.
- **Reportes de "Banderas Rojas"**: Interfaz interactiva en Telegram con interpretación cognitiva de hallazgos técnicos y propuestas de remediación automatizadas.

## [2.1.2] - 2026-03-22 (Fase 16 - Warden: Infraestructura Local & Synology)

### Añadido
- **Agente Warden (Expert)**: Especialista en la gestión de infraestructura crítica, redes locales seguras y almacenamiento masivo (NAS).
- **NetworkMonitor Proactivo**: Vigilancia constante del túnel VPN (Tailscale/Wireguard) con alertas críticas ante desconexiones de red segura.
- **Extensión SynologyClient**: Control total de la salud del hardware NAS, orquestación de Docker en Container Manager y actualizaciones críticas de DSM.
- **Confirmación de Acciones Críticas**: Implementación de botones Inline de Telegram para la validación manual de acciones de alto impacto (reinicio de servidores, etc.).

## [2.1.1] - 2026-03-22 (Fase 15 - Chronos: Ciclo de Vida & Poda de Datos)

### Añadido
- **Fase 15: Chronos Agent**: Especialista en la higiene del ecosistema; gestiona la rotación de logs técnica y la poda de la base de datos vectorial (VectorDB).
- **Fase 15.1: WorkspaceManager**: Motor de aislamiento de entornos de trabajo (Sandboxing) que garantiza permisos Zero-Trust a nivel de sistema de archivos.

## [2.1.0] - 2026-03-21 (Fase 21.6 - Trazabilidad de Origen & Context Envelope)

### Añadido
- **Estándar de Origen (Context Envelope)**: Implementación de la interfaz `NexoMessageEnvelope` para normalizar todas las entradas al sistema con UUIDs únicos y metadata de proveniencia.
- **Middleware del Gateway (Hermes)**: Nuevo interceptor proactivo que encapsula cada mensaje de Telegram en una cápsula de contexto estándar.
- **Zero Trust (Sentinel integration)**: Implementación de validación estricta de `senderId` contra lista blanca (`AUTHORIZED_USERS`) en el punto de entrada, con registro de alertas críticas en Sentinel para intentos bloqueados.
- **Aislamiento de Memoria por Hilo**: El historial de conversación ahora se segmenta mediante claves compuestas (`provider_channel_thread`), garantizando que no haya cruces de contexto entre hilos o grupos.
- **Trazabilidad de Agentes**: Inyección de metadata del sobre en cada línea de ejecución de herramientas y logs de agentes para auditorías forenses precisas.

## [2.0.0] - 2026-03-20 (Fase 23 - Centro de Control Nexo v2.0)

### Añadido

- **Reconstrucción Total del Panel**: Migración de `nexo-panel` al diseño "The Sovereign Terminal" basado en Stitch.
- **Sistema de Diseño "Digital Bunker"**: Implementación de tokens de color, tipografía y efectos de alta fidelidad.
- **Navegación Multidimensional**: 7 nuevas vistas (Core, Brain, Agents, Lab, Sentinel, Config, Abaddon).
- **Integración Nativa Firebase**: Configuración de Hosting y Firestore para persistencia remota.

## [1.9.0] - 2026-03-15 (Fase 22 - Deterministic Hardware Monitoring)

### Añadido

- **Módulo SystemMonitor**: Implementación de cálculo de CPU mediante deltas de ticks (real-time) eliminando la dependencia de Load Average.
- **Telemetría de Alta Fidelidad**: Sincronización precisa entre el hardware real de la máquina y el indicador visual del Command Center.
- **Robustez de Canal (Hermes)**: Corrección de lints y métodos de estado (`getMemoryStatus`, `getBotInfo`, `setGateway`).
- **Nexo Voice Fix**: Actualización de sintaxis `grammY` para el envío de respuestas de audio.

## [1.8.0] - 2026-03-15 (Fase 21 - Módulo Hermes: Resiliencia & UX)

### Añadido

- **Refactorización Módulo Hermes**: Migración completa de Telegraf a `grammY` para una gestión de sesiones y middlewares superior.
- **Resiliencia API (Throttler)**: Implementación de `@grammyjs/transformer-throttler` con límites de 30/s global y 1/s por chat para evitar baneos y gestionar el error 429.
- **UX Fluida (Answer Callback)**: Middleware interceptor global que responde instantáneamente a cada pulsación de botón, eliminando el lag visual en el móvil.
- **Edición de Mensajes In-situ**: Abstracción `editStatus` para actualizar estados ("⏳ Procesando...", "✅ Completado") sin inundar el chat de mensajes.
- **Seguridad de Webhook (Transport Layer)**: Validación de `X-Telegram-Bot-Api-Secret-Token` para garantizar la legitimidad de las peticiones entrantes.
- **Enrutador de Contexto (Sessions)**: Soporte para flujos de conversación complejos y estados críticos (Protocolo Abaddon).

## [1.7.6] - 2026-03-15 (Fase 11 - Brain Accuracy Fix)


### Corregido

- **Sincronización Real de Modelos**: Se ha eliminado la información estática / placeholders (Ollama, Anthropic, etc.) de la interfaz del Command Center.
- **Detección Dinámica de Configuración**: El frontend ahora consume dinámicamente los proveedores y modelos definidos en el archivo `.env` a través de la API.
- **Corrección de Fallback**: Actualización de los valores por defecto en el constructor de `LLMEngine` para reflejar el stack real (Groq Llama 3.3).

## [1.7.5] - 2026-03-15 (Fase 11 - Nexo Brain Monitor)

### Añadido

- **Módulo "Brain"**: Nueva sección en el Command Center para el monitoreo y control de LLMs.
- **Seguimiento de Latencia**: Medición en tiempo real del tiempo de respuesta de cada proveedor (Google, OpenRouter).
- **Historial de Razonamiento**: Stream visual de las últimas 10 peticiones procesadas por el asistente.
- **Aislamiento Cerebral (Emergency Block)**: Control granular para bloquear/desbloquear el acceso a Internet del motor LLM desde la UI.
- **Dashboard Premium**: Diseño futurista en color "Brain Violet" (#8B5CF6) con Glassmorphism y animaciones de Framer Motion.
- **Endpoints Brain API**: Soporte para `/api/brain/status` y `/api/brain/toggle-block`.

## [1.7.0] - 2026-03-15 (Fase 10 - Command Center Backend)

### Añadido

- **Command Center API**: Servidor REST seguro (`127.0.0.1:3001`) para telemetría y control.
- **Autenticación HMAC-SHA256**: Validación estricta Zero Trust para Telegram Mini Apps.
- **Botón del Pánico (Emergency Kill Switch)**: Aislamiento instantáneo de MCPs y red LLM.
- **Telemetría Avanzada**: Monitoreo de CPU, RAM, Docker, VectorDB y consumo diario de tokens.

## [1.6.5] - 2026-03-14 (Fase 9 - Refuerzo DevSecOps)

### Añadido

- **DLP Sanitizer (Intercepción)**: Ofuscación proactiva de datos sensibles (CR, Emails, Keys) antes de salir a MCPs.
- **Ciclo de Vida Efímero (TTL)**: Auto-apagado de servidores MCP tras 60s de inactividad (optimización de recursos).
- **Network Guard (Aislamiento Docker)**: Ejecución de MCPs en redes internas aisladas sin acceso a Internet.
- **Sistema de Estado Sentinel**: Informe proactivo de salud del sistema vía Telegram (`getSystemStatus`).

## [1.6.0] - 2026-03-14 (Fase 9 - MCP Secure Integration)

### Añadido

- **Secure MCP Client**: Cliente estandarizado para consumir herramientas de terceros (stdio/SSE).
- **Aduana de Herramientas**: Filtrado proactivo de herramientas MCP mediante `mcp_allowlist.json`.
- **Tool Circuit Breaker**: Interruptor de seguridad que aísla servidores MCP fallidos tras 3 errores o timeout.
- **Protección Anti-DoS**: Validación del tamaño de recursos MCP para proteger el contexto comercial del LLM.

## [1.5.0] - 2026-03-14 (Fase 8 - Sentinel Monitoring)

### Añadido

- **Sentinel System**: Monitorización pasiva de logs en tiempo real para detección de anomalías.
- **Threat Knowledge Base**: Base de datos de amenazas traducida a lenguaje humano.
- **Alertas en Telegram**: Notificaciones inmediatas de bloqueos o intentos de intrusión.
- **Defensa ante Ofuscación**: Normalización de texto para detectar comandos camuflados (ej. `s.u.d.o`).

## [1.4.5] - 2026-03-14 (Fase 7 - Agente de Calidad Determinista)

### Añadido

- **Deterministic Security Auditor**: Chequeo nativo de permisos y integridad de secretos (.env) sin latencia.
- **Functional Auditor**: Monitorización de puertos vitales (Port 3000) y métricas de RAM/Heap.
- **Intelligent Diagnostics**: Activación del LLM solo ante fallos detectados para análisis de causa raíz.
- **QALogger**: Persistencia estructurada de auditorías con evidencia técnica y latencias.

## [1.4.0] - 2026-03-14 (Fase 6 - Zero Trust Desktop Node)

### Añadido

- **Desktop Node (Cliente Certificado)**: Nuevo cliente local desacoplado que opera bajo modelo de confianza cero.
- **Handshake de Seguridad**: Vinculación mediante `NEXO_NODE_TOKEN` inyectado por entorno.
- **Intercepción de Comandos**: Motor de seguridad que bloquea proactivamente comandos peligrosos (`rm`, `sudo`, etc.).
- **Auditoría Forense**: Registro detallado de todas las operaciones en `logs/node-audit.log` con zona horaria local (Europe/Madrid).
- **Delegación Inteligente**: El Gateway ahora delega la ejecución al nodo certificado si está presente, aumentando la seguridad.
- **Manejo de Permisos (TCC)**: Sistema de degradación elegante para permisos del SO (ej. grabación de pantalla).

## [1.3.0] - 2026-03-14 (Fase 5)

### Añadido

- **Motor Proactivo (CRON)**: Planificador de tareas dinámico integrado en el Gateway.
- **Superficie de Webhooks**: Endpoint seguro (`PORT+1`) para recibir eventos externos procesados por IA.
- **Live Canvas (A2UI)**: Dashboard en tiempo real con validación estricta de esquemas Zod.
- **Validación Estricta**: Blindaje de contratos de datos para todos los componentes visuales.
- **Mobile Pairing Core**: Infraestructura y contratos para vinculación de nodos móviles.

## [1.2.0] - 2026-03-13 (Fase 4 - Audio & Memoria)

### Añadido

- **Multi-Agent Orchestration**: Sistema de sesiones con comunicación inter-agente y control de recursividad.
- **Dynamic Skills Registry**: Carga modular de herramientas desde archivos externos sin tocar el core.
- **Zero-Trust Network**: Validador de seguridad para Tailscale y blindaje de interfaces de red.
- **LLM Context Awareness**: Nexo ahora es consciente de sus herramientas de sesión y habilidades dinámicas.

## [1.1.5] - 2026-03-13 (Fase 3 - Gateway CORE & Cloud Security)

### Añadido

- **Central Control Plane**: Implementación del orquestador WebSocket para eventos y sesiones.
- **Tailscale Network Guard**: Validación de seguridad redundante; bloqueo automático si no está anclado a 127.0.0.1 en modo Funnel.
- **Session Dispatcher**: Enrutamiento nativo de acciones (sessions.list, sessions.history).
- **Presence Engine**: Sistema de heartbeats para nodos conectados y clientes activos.

## [1.1.0] - 2026-03-13 (Fase 2)

### Añadido

- **Nodos Locales**: Implementación de `system.run` y `system.notify` (con AppleScript).
- **Control de Navegador (CDP)**: Módulo `NexoBrowser` para capturas de pantalla y navegación directa.
- **A2UI Foundations**: Definición de eventos `canvas.push` y broadcast en el Gateway.
- **Seguridad Avanzada**: Módulo `NexoSecurity` integrado en todos los puntos de entrada (Telegram/Gateway).
- **Tool Calling**: Nexo ahora decide proactivamente cuándo usar la terminal, el navegador o el canvas.

## [1.0.0] - 2026-03-13 (Fase 1)

### Añadido

- **Gateway WebSocket**: Servidor base para el plano de control central.
- **Motor LLM**: Integración con Groq y OpenRouter con lógica de failover.
- **Módulo Telegram**: Primer canal de comunicación con sistema de seguridad DM Pairing.
- **Persistencia**: Estructura de carpetas en `~/.nexo` para logs y allowlist.
- **Stubs**: Definición de interfaces para herramientas de nodo, habilidades y acceso remoto.
- **Configuración**: Setup de TypeScript, Node.js y pnpm.
