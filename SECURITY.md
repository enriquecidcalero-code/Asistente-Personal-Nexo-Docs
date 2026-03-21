# 🔐 Modelo de Seguridad de Nexo: La Fortaleza Progresiva

Nexo está construido bajo la premisa de que **"La seguridad no se añade al final; es el cimiento sobre el que se construye la funcionalidad"**. Este documento explica cómo cada componente de Nexo contribuye a un ecosistema blindado y soberano.

---

## 🏛️ El Principio de "Privilegio Mínimo" y "Confianza Cero"

En Nexo, partimos de un estado de **aislamiento absoluto**. Cada nueva "habilidad" o canal de comunicación que abrimos debe pasar por múltiples capas de validación criptográfica y lógica.

### 🛡️ Nivel 1: El Perímetro Humano (SenderId Whitelist) - [NUEVO PHASE 21]

A diferencia de los bots tradicionales, Nexo no responde a desconocidos por defecto.

* **Mecanismo**: Validación estricta de `senderId` contra una lista blanca (`AUTHORIZED_USERS`) en el punto de entrada de Hermes.
* **Zero Trust**: Los intentos fallidos se bloquean y se registran como alertas críticas en Sentinel para auditoría forense.

### 🛡️ Nivel 2: La Red Invisible (Tailscale Guard)

El Gateway de Nexo es invisible en la Internet pública.

* **Mecanismo**: El sistema monitoriza las interfaces de red. Si detecta que no está bajo la protección de Tailscale o protocolos seguros, entra en modo **Lockdown**.

### 🛡️ Nivel 3: El Brazo Ejecutor Blindado (Desktop Node)

El servidor que procesa el lenguaje (Gateway) no es el mismo que ejecuta acciones en tu máquina.

* **Mecanismo**: El **Desktop Node** certificado opera de forma independiente, bloqueando proactivamente comandos de terminal sensibles (`sudo`, `rm`, `mkfs`) mediante un motor de reglas nativo.

### 🛡️ Nivel 4: Context Envelope & Aislamiento de Memoria - [NUEVO PHASE 21.6]

Aseguramos que no haya cruces de datos entre diferentes hilos o usuarios.

* **Encapsulamiento**: Cada mensaje se envuelve en un `NexoMessageEnvelope` con UUIDs únicos y metadata de origen.
* **Aislamiento de Hilos**: El historial se segmenta mediante claves compuestas (`provider_channel_thread`), garantizando la estricta privacidad de cada contexto de conversación.

### 🛡️ Nivel 5: Soberanía de Datos (SQLite Local) - [NUEVO PHASE 21.5]

Hemos eliminado la dependencia de servicios Cloud (como Firebase) para la persistencia de datos sensibles.

* **Mecanismo**: Uso de **SQLite Local** con `better-sqlite3`. Toda la conversación, logs y secretos residen exclusivamente en el hardware del usuario.
* **Impacto**: Soberanía total. Si desconectas Internet, tus datos siguen siendo accesibles y seguros localmente.

### 🛡️ Nivel 6: Vigilancia Sentinel 2.0 (Auto-Heal & Anti-Ofuscación)

Sentinel actúa como un EDR (Endpoint Detection and Response) simplificado para tu asistente.

* **Motor Anti-Ofuscación**: Normaliza las cadenas de texto antes de auditarlas, detectando comandos camuflados (ej: `s u d o`).
* **Protocolo Auto-Heal**: Si detecta fallos en el Gateway, Sentinel limpia procesos huérfanos y reinicia el sistema para asegurar la disponibilidad.

---

## 🔬 Capas de Auditoría e Integridad

Nexo mantiene un rastro forense inalterable en:

* `.nexo_data/nexo_core_debug.log`: Registro detallado de cada decisión de seguridad.
* `.nexo_data/security/mcp_allowlist.json`: El "pasaporte" de herramientas. Solo lo que está aquí puede ser ejecutado por la IA.
* `Nexo Vault`: Un almacén cifrado para gestionar identidades OAuth de forma centralizada sin exponer secretos en plano.

---

> [!IMPORTANT]
> La seguridad de Nexo ha evolucionado hacia un modelo **Autorreparable y Soberano**. El sistema no solo detecta amenazas, sino que garantiza que tus datos nunca abandonen tu control físico.
