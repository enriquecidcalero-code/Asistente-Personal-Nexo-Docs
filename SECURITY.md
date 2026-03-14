# 🔐 Modelo de Seguridad de Nexo: La Fortaleza Progresiva

Nexo está construido bajo la premisa de que **"La seguridad no se añade al final; es el cimiento sobre el que se construye la funcionalidad"**. Este documento explica cómo cada componente de Nexo contribuye a un ecosistema blindado.

---

## 🏛️ El Principio de "Privilegio Mínimo" y "Confianza Cero"

En Nexo, partimos de un estado de **aislamiento absoluto**. Cada nueva "habilidad" o canal de comunicación que abrimos debe justificar su existencia y pasar por múltiples capas de validación.

### 🛡️ Nivel 1: El Perímetro Humano (DM Pairing)
Nadie puede interactuar con el cerebro de Nexo sin una validación física previa.
*   **Mecanismo**: Si un ID de Telegram desconocido contacta al bot, Nexo genera un código efímero en la **terminal física del propietario**.
*   **Objetivo**: Evitar accesos no autorizados incluso si el bot es descubierto en la red de Telegram.

### 🛡️ Nivel 2: La Red Invisible (Tailscale Guard)
El Gateway de Nexo está diseñado para ser invisible en la Internet pública.
*   **Mecanismo**: El sistema monitoriza las interfaces de red. Si detecta que no está bajo la protección de Tailscale o protocolos seguros, entra en modo **Lockdown**.

### 🛡️ Nivel 3: El Brazo Ejecutor Blindado (Desktop Node)
El servidor que habla contigo no es el mismo que ejecuta tus archivos.
*   **Mecanismo**: El **Desktop Node** certificado opera de forma independiente. Bloquea proactivamente comandos de terminal sensibles (`sudo`, `rm`, `mkfs`) antes de que se ejecuten.

### 🛡️ Nivel 4: Vigilancia Sentinel 2.0 (Autonómia y Detección) - [MEJORADO v1.7.0]
Sentinel es ahora un administrador de salud proactivo además de un vigilante.
*   **Protocolo Auto-Heal**: Sentinel monitoriza la salud del Gateway cada 10s. Si el sistema cae, el protocolo de auto-reanimación se activa, limpia puertos bloqueados y reinicia los servicios sin intervención humana.
*   **Motor Anti-Ofuscación**: Normaliza las cadenas de texto antes de auditarlas, eliminando ruidos (`.`, `-`, `_`) y colapsando caracteres espaciados que intentan evadir las firmas de seguridad.
*   **Reporting VITAL**: Genera informes de integridad firmados con el estado real del hardware y el software.

### 🛡️ Nivel 5: Aduana MCP y Protección de Datos - [MEJORADO v1.7.0]
La expansión universal mediante MCP cuenta con capas de protección profunda:
*   **Instancias Efímeras (Ephemeral Mode)**: Reducción de la superficie de exposición al levantar servidores MCP solo durante la ejecución y cerrarlos automáticamente tras 60s de inactividad.
*   **DLP Sanitizer (Data Loss Prevention)**: Un interceptor inspecciona los argumentos enviados a herramientas externas (como Perplexity o Firecrawl) para asegurar que no se fugue información privada o credenciales sensibles.
*   **Circuit Breaker**: Mecanismo de seguridad que "corta el flujo" hacia extensiones que presentan fallos sospechosos o latencias extremas.

---

## 🔬 Capas de Auditoría
Nexo mantiene un rastro forense inalterable en:
*   `~/.nexo/logs/node-audit.log`: Registro cronológico de cada interacción y decisión de seguridad.
*   `~/.nexo/security/threat_kb.json`: Inteligencia de amenazas local que traduce eventos técnicos a lenguaje humano comprensible.

> [!IMPORTANT]
> La seguridad de Nexo ha evolucionado hacia un modelo **Autorreparable**. El sistema no solo detecta amenazas, sino que es capaz de mantener su propia disponibilidad operativa frente a fallos y ataques.
