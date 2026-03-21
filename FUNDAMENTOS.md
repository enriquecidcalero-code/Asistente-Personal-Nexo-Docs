# 🧠 Fundamentos Técnicos: Cómo funciona Nexo

Este documento profundiza en la ingeniería de vanguardia detrás del **Asistente Personal Nexo (Open Gravity)**, detallando los subsistemas core y las mejoras de la Fase 21-23.

---

## 🛰️ 1. Gateway Central (Hermes): El Plano de Control

El Gateway es el orquestador principal del sistema, recientemente refactorizado para mayor resiliencia.

* **Protocolo grammY**: Sustitución de Telegraf por grammY para un manejo superior de middlewares y sesiones.
* **Answer Callback Instantáneo**: Intercepción global de callbacks para feedback inmediato al móvil (eliminación de lag visual).
* **Throttler Proactivo**: Gestión automática de rate limits (30 msg/s global) y resolución autónoma del error 429.

### 🛡️ 1.1. Context Envelope & Trazabilidad (Phase 21.6)

Cada entrada de datos al sistema se normaliza mediante la interfaz `NexoMessageEnvelope`.

* **Metadata de Origen**: UUID único para cada mensaje, identificación de proveedor (`TELEGRAM`), canal y hilo de conversación.
* **Aislamiento de Memoria**: Segmentación de historial basado en claves compuestas (`provider_channel_thread`), previniendo cruces de contexto involuntarios.

---

## 🤖 2. Motor LLM e Inteligencia Adaptativa (Brain)

El motor cognitivo de Nexo (`LLMEngine`) prioriza la velocidad y la fiabilidad.

* **Failover Multi-Provider**: Intento primario con **Groq** (Llama-3.3-70b/8b) para baja latencia (<500ms) y respaldo automático con **OpenRouter** (Claude/GPT).
* **Cerebro Morfológico**: El motor es consciente de sus herramientas de sesión y habilidades dinámicas, decidiendo proactivamente cuándo usar la terminal, el navegador o herramientas MCP.

---

## 📀 3. Persistencia Soberana (SQLite Local) - [PHASE 21.5]

Nexo ha pasado de una arquitectura basada en la nube a una **totalmente local**.

* **Motor better-sqlite3**: Persistencia síncrona y de alto rendimiento.
* **Independencia de Nube**: Eliminación completa de Firebase para el almacenamiento de sesiones y mensajes, garantizando que el asistente funcione al 100% sin conexión externa o configuración cloud compleja.
* **Tablas Unificadas**: Estructura relacional para una recuperación eficiente de contextos de conversación masivos.

---

## 🔑 4. Nexo Vault: Gestor Centralizado de Secretos

El sistema **Nexo Vault** actúa como el gestor de identidades y tokens OAuth.

* **Centralización**: Control unificado de flujos de autenticación de terceros (Google, GitHub, ElevenLabs).
* **Cifrado Local**: Los tokens se almacenan cifrados en el hardware del usuario, nunca se exponen en texto plano en el Gateway ni en el Panel.

---

## 🖥️ 5. Nexo OS Panel: Terminal Soberano v2.0

La interfaz visual ha sido reconstruida íntegramente para ofrecer control total.

* **Telemetría de Hardware**: Cálculo de CPU mediante deltas de ticks y RAM en tiempo real, sincronizando el estado físico de la máquina con la interfaz.
* **Vistas Multidimensionales**: 7 nuevas secciones (Core, Brain, Agents, Lab, Sentinel, Config, Abaddon) para la supervisión granular del asistente.
* **Dashboard Futurista**: Diseño de alta fidelidad con Glassmorphism y animaciones fluidas para una experiencia UX premium.

---

## 👁️ 6. Sistema Sentinel: Vigilancia Vital

Sentinel es el guardián autónomo del sistema.

* **Auto-Reanimación (Auto-Heal)**: Si detecta la caída de un servicio vital (Puerto 3000 o 3001), Sentinel mata procesos huérfanos y los reinicia de forma autónoma.
* **Motor Forense**: Detección de intrusiones en logs en tiempo real y bloqueo de escalada de privilegios.

---

> El desarrollo de Nexo se basa en la robustez y la soberanía: el sistema está diseñado para ser indetectable, autoprotegido y 100% controlado por el usuario.
