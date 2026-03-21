# 🌌 Nexo (Open Gravity) - Documentación Central

> **El plano de control central para tu asistente personal de IA soberano.**

Bienvenido al repositorio oficial de documentación del **Asistente Personal Nexo (Open Gravity)**. Este proyecto es un sistema de orquestación de IA avanzado, diseñado para ejecutarse localmente proporcionando máxima privacidad, control y una arquitectura de confianza cero.

---

## 🛡️ Filosofía de Desarrollo: Seguridad Total por Diseño

A diferencia de otros asistentes que priorizan la funcionalidad y luego intentan "parchear" la seguridad, Nexo ha sido construido con una **mentalidad de Fortificado Progresivo**.

Nuestra base estratégica ha sido:

1. **Restricción Total (Fase 1)**: Comenzar en un entorno completamente sellado donde nada puede entrar ni salir sin autorización explícita (DM Pairing).
2. **Base Robusta**: Crear un núcleo (Gateway) que no confía en nadie, ni siquiera en el nodo que ejecuta los comandos.
3. **Apertura Controlada**: A medida que añadimos habilidades (Navegación, Audio, MCP), cada una pasa por una "aduana" de seguridad (Sentinel, Allowlists, Zod Validation) para asegurar que el sistema nunca pierda su integridad.

---

## 🚀 Análisis Detallado de Fases

Nexo ha evolucionado a través de múltiples hitos críticos, cada uno añadiendo una capa de blindaje e inteligencia:

### [Fase 1-5] El Sistema Nervioso y el Perímetro

* **Seguridad**: Implementación del **DM Pairing** y **Tailscale Network Guard**.
* **UX**: Primer Gateway WebSocket y **Live Canvas (A2UI)** para dashboard en tiempo real.
* **Impacto**: Blindaje total contra extraños y visualización de datos estricta mediante Zod.

### [Fase 6-9] Confianza Cero y Vigilancia Activa

* **Seguridad**: Creación del **Desktop Node** (aislamiento de ejecución) y el módulo **Sentinel**.
* **Inteligencia**: Integración de **MCP (Model Context Protocol)** bajo una aduana de seguridad (`allowlist.json`).
* **Impacto**: Separación física de la "mente" y el "brazo", con monitorización pasiva 24/7.

### [Fase 10-11] Gestión de Secretos y Salud Cognitiva

* **Seguridad**: **Nexo Vault** para gestión centralizada y cifrada de tokens OAuth.
* **Monitoreo**: Dashboard de **Brain Monitor** para seguimiento de latencias LLM y failover en tiempo real.
* **Impacto**: Control total sobre las identidades externas y visibilidad del "pensamiento" del asistente.

### [Fase 21] Hermes (UX de Alta Resiliencia)

* **Infraestructura**: Migración íntegra a **grammY** con gestión avanzada de sesiones.
* **Resiliencia**: Implementación de **Throttler** (30/s) y manejo automático del error 429 (Too Many Requests).
* **UX**: Feedback instantáneo (Answer Callback) y edición in-situ de mensajes para una conversación fluida.

### [Phase 21.5] Soberanía de Datos (Local SQLite)

* **Persistencia**: Migración completa de Firebase a **SQLite Local** (`better-sqlite3`).
* **Rendimiento**: Persistencia síncrona, de alto rendimiento y 100% privada sin dependencias externas de nube.
* **Impacto**: Nexo ahora es un sistema **100% Autónomo** y distribuible sin necesidad de configuración Cloud.

### [Phase 21.6] Trazabilidad y Contexto (Envelope)

* **Protocolo**: Implementación de `NexoMessageEnvelope` para normalizar cada entrada con UUIDs y metadata de origen.
* **Seguridad**: Aislamiento de memoria por hilo (`provider_channel_thread`) garantizando que no haya cruces de contexto.
* **Auditoría**: Trazabilidad completa de agentes para análisis forenses precisas.

### [Fase 22-23] Monitorización de Hardware y Terminal Soberano

* **Telemetría**: Cálculo de CPU mediante deltas de ticks y RAM en tiempo real.
* **UI/UX**: **Panel v2.0 (The Sovereign Terminal)** con 7 vistas multidimensionales (Core, Brain, Agents, Lab, Sentinel, Config, Abaddon).
* **Impacto**: Una interfaz de usuario de grado militar para el control total de la infraestructura.

---

## 🗺️ Guía de Documentación

1. [**📋 PRD (Requisitos)**](PRD.md): Definición detallada, objetivos y visión del producto.
2. [**🏗️ Arquitectura**](ARQ.md): Diagramas técnicos y stack tecnológico (Node/TS/pnpm).
3. [**🧠 Fundamentos Técnicos**](FUNDAMENTOS.md): **[NUEVO]** Explicación profunda de la ingeniería: Gateway, Motores LLM, Failover y Lógica de Nodos.
4. [**📅 Plan Maestro**](PLAN.md): Roadmap histórico y próximos hitos del proyecto.
5. [**🔐 Seguridad**](SECURITY.md): El manual profundo de Sentinel, Node Protection y Pairing.
6. [**📜 Changelog**](CHANGELOG.md): Historial de versiones y mejoras implementadas.
7. [**🔌 Espec. Técnicas MCP**](MCP_TECH_SPEC.md): Arquitectura Model Context Protocol, Aduana Digital y Circuit Breakers.

---

*Documentación mantenida y evolucionada por Antigravity (IA).*
