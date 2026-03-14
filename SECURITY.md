# 🔐 Modelo de Seguridad de Nexo

Nexo está construido bajo la filosofía de que "La seguridad no es una capa, es el núcleo". Implementamos múltiples defensas profundas para proteger tu entorno local.

## 🛡️ Niveles de Protección

### 1. DM Pairing (Telegram)
Nadie puede hablar con Nexo a menos que esté en la `allowlist.json`.
- Al recibir un mensaje de un ID desconocido, Nexo guarda silencio pero genera un **Pairing Code** en la consola local.
- El usuario debe proporcionar ese código exacto para ser vinculado.
- Una vez vinculado, el ID es persistente.

### 2. Zero Trust Desktop Node
La ejecución de comandos no ocurre en el servidor web, sino en un proceso de nodo local separado.
- **Handshake**: El nodo debe autenticarse con el Gateway usando un token asimétrico.
- **Whitelist de Comandos**: Nexo tiene un motor que intercepta comandos de terminal. Si intentas ejecutar algo como `rm -rf /` o `sudo`, el comando es bloqueado instantáneamente antes de llegar al sistema operativo.

### 3. Sentinel (Detección de Amenazas)
El Sentinel es un watchdog pasivo que no consume recursos de IA.
- Lee en tiempo real los logs en `~/.nexo/logs/node-audit.log`.
- Utiliza reglas Regex avanzadas para detectar:
    - Ofuscación de comandos (ej: `s.u.d.o`).
    - Intentos de fuerza bruta en los puertos del Gateway.
    - Caídas de servicios críticos.
- Al detectar una amenaza, envía una **Alerta de Seguridad** de alta prioridad al canal de Telegram autorizado.

### 4. Aduana de Herramientas MCP
Con la integración del Model Context Protocol, Nexo puede usar herramientas de terceros. 
- **Allowlist estricto**: Ninguna herramienta MCP puede ejecutarse si no ha sido autorizada previamente en `mcp_allowlist.json`.
- **Validación de Datos**: Todos los inputs enviados a las herramientas son validados mediante esquemas Zod para prevenir inyecciones de código.

---

## 🔬 Auditoría y Logs
La persistencia de seguridad se guarda en carpeta oculta del sistema para mayor protección:
- `~/.nexo/workspace/allowlist.json`
- `~/.nexo/logs/node-audit.log`
- `~/.nexo/security/mcp_allowlist.json`

> [!WARNING]
> Nunca compartas tu `NEXO_NODE_TOKEN` ni los archivos dentro de `~/.nexo/security/`.
