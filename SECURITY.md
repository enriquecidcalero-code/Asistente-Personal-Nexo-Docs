# 🔐 Modelo de Seguridad de Nexo: La Fortaleza Progresiva

Nexo está construido bajo la premisa de que **"La seguridad no se añade al final; es el cimiento sobre el que se construye la funcionalidad"**. Este documento explica cómo cada componente de Nexo contribuye a un ecosistema blindado.

---

## 🏛️ El Principio de "Privilegio Mínimo" y "Confianza Cero"

En Nexo, partimos de un estado de **aislamiento absoluto**. Cada nueva "habilidad" o canal de comunicación que abrimos debe justificar su existencia y pasar por múltiples capas de validación.

### 🛡️ Nivel 1: El Perímetro Humano (DM Pairing)
Nadie puede interactuar con el cerebro de Nexo sin una validación física previa.
*   **Mecanismo**: Si un ID de Telegram desconocido contacta al bot, Nexo genera un código efímero en la **terminal física del propietario**. Solo si ese código se devuelve correctamente, se añade a la `allowlist.json`.
*   **Objetivo**: Evitar accesos no autorizados incluso si el bot es descubierto en la red de Telegram.

### 🛡️ Nivel 2: La Red Invisible (Tailscale Guard)
El Gateway de Nexo está diseñado para ser invisible en la Internet pública.
*   **Mecanismo**: El sistema monitoriza las interfaces de red. Si detecta que no está bajo la protección de Tailscale o protocolos seguros, entra en modo **Lockdown**.
*   **Objetivo**: Eliminar la superficie de ataque frente a escaneos de puertos globales.

### 🛡️ Nivel 3: El Brazo Ejecutor Blindado (Desktop Node)
El servidor que habla contigo no es el mismo que ejecuta tus archivos.
*   **Mecanismo**: El **Desktop Node** certificado opera de forma independiente. Antes de ejecutar cualquier comando de terminal, un motor de reglas nativo analiza la cadena de texto.
*   **Bloqueo Preventivo**: Si detecta comandos como `sudo`, `rm`, `mkfs`, o redirecciones de streams peligrosas, el comando muere antes de tocar el Shell.
*   **Objetivo**: Contener posibles fugas de lógica del LLM que pudieran intentar dañar el sistema de archivos.

### 🛡️ Nivel 4: Vigilancia Sentinel (Detección de Anomalías)
Incluso con muros altos, necesitamos un centinela.
*   **Mecanismo**: Un watchdog pasivo analiza los logs forenses (`node-audit.log`) cada segundo. Utiliza patrones heurísticos para detectar **Ofuscación** (ej. `s.u.d.o`, encoded strings) o comportamientos anómalos.
*   **Objetivo**: Detección y respuesta inmediata ante ataques persistentes o bugs de seguridad.

### 🛡️ Nivel 5: Aduana de Herramientas MCP
La expansión de Nexo mediante el protocolo MCP se realiza bajo un modelo de **Lista Blanca**.
*   **Mecanismo**: Cada servidor MCP externo debe estar registrado en la `mcp_allowlist.json`. Sin esta firma electrónica, la IA tiene prohibido por código invocar cualquier función externa.
*   **Objetivo**: Garantizar que la IA solo use herramientas seguras y aprobadas por el humano.

---

## 🔬 Capas de Auditoría
Nexo mantiene un rastro forense inalterable en:
*   `~/.nexo/logs/node-audit.log`: Cada comando, cada respuesta, cada éxito y cada bloqueo.
*   `~/.nexo/security/`: Almacén de tokens de sesión y certificados de nodo.

> [!IMPORTANT]
> Nexo ha sido diseñado para que, incluso en el caso hipotético de una brecha en la capa de IA, el sistema operativo subyacente permanezca protegido por reglas deterministas e inviolables.
