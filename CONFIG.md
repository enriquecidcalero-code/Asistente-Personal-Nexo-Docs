# ⚙️ Guía de Configuración de Nexo

Nexo utiliza variables de entorno para gestionar las conexiones con proveedores externos y la configuración de seguridad del Gateway.

## 📄 Archivo `.env`

Crea un archivo `.env` en la raíz del proyecto basándote en el siguiente esquema:

```bash
# Token de Telegram (@BotFather)
TELEGRAM_TOKEN=tu_token_aqui

# Proveedores de LLM
GROQ_API_KEY=tu_llave_groq
OPENROUTER_API_KEY=tu_llave_openrouter

# Configuración del Gateway
PORT=3000

# Seguridad
# Este código es el inicial para el handshake de emparejamiento.
# Se recomienda usar uno generado aleatoriamente.
PAIRING_CODE=123456

# Nexo Node (Opcional si se usa Desktop Node)
NEXO_NODE_TOKEN=token_seguro_para_nodos
```

## 📂 Directorios de Datos

Nexo crea y gestiona automáticamente una carpeta oculta de datos llamada `.nexo_data` (o `~/.nexo` dependiendo de la versión) que contiene:

| Carpeta | Propósito |
| :--- | :--- |
| `workspace/` | Almacena los IDs de Telegram autorizados y scripts de habilidades. |
| `sessions/` | Historial de conversaciones cifrado y persistente. |
| `logs/` | Registro de actividad para el sistema Sentinel. |
| `security/` | Whitelists de herramientas MCP y tokens de confianza. |

## 🚀 Requisitos Técnicos
- **Node.js**: Versión 20 o superior.
- **pnpm**: Gestor de paquetes recomendado para mayor velocidad y ahorro de espacio.
- **Internet**: Requerido para la conexión con los LLMs y Telegram (a menos que se usen modelos locales en el futuro).

## 📡 Puertos por Defecto
- **3000**: Gateway WebSocket principal.
- **3001**: Puerto espejo para comunicaciones internas del Desktop Node.
- **3002**: (Opcional) Puerto para webhooks entrantes de servicios externos.
