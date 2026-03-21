# ⚙️ Guía de Configuración de Nexo

Nexo utiliza variables de entorno para gestionar las conexiones con proveedores externos, la persistencia local y la configuración de seguridad del Gateway.

---

## 📄 Archivo `.env`

Crea un archivo `.env` en la raíz del proyecto basándote en el siguiente esquema (puedes usar `.env.example` como plantilla):

```bash
# --- NEXO CORE CONFIGURATION ---
PORT=3000
ADMIN_TELEGRAM_ID=tu_id_de_telegram_aqui
TELEGRAM_TOKEN=tu_bot_token_aqui (de @BotFather)

# --- LLM PROVIDERS ---
GROQ_API_KEY=tu_clave_de_groq_aqui (Llama 3.3)
OPENROUTER_API_KEY=tu_clave_de_openrouter_aqui (Claude/GPT)

# --- MCP: SERVICE KEYS ---
PERPLEXITY_API_KEY=tu_clave_perplexity
FIRECRAWL_API_KEY=tu_clave_firecrawl
ELEVENLABS_API_KEY=tu_clave_elevenlabs

# --- PERSISTENCE (Soberanía de Datos) ---
# Nexo prefiere SQLite para una persistencia 100% local y soberana.
SQLITE_DB_PATH=./.nexo_data/nexo.db

# --- SECURITY ---
MCP_ALLOWLIST_PATH=./.nexo_data/security/mcp_allowlist.json
DLP_STRICT_MODE=true (Previene la fuga de información sensible)

# --- PHASE 23: NEXO OS PANEL ---
WEBAPP_URL=http://localhost:5173 (O tu IP de Tailscale)
```

---

## 📂 Estructura de Datos (`.nexo_data/`)

Nexo gestiona automáticamente una carpeta de datos persistentes que contiene el estado vital del sistema:

| Directorio / Archivo | Propósito |
| :--- | :--- |
| `nexo.db` | Base de datos SQLite unificada para sesiones, mensajes y usuarios. |
| `security/` | Contiene los listados de herramientas autorizadas (MCP Allowlist). |
| `logs/` | Registro de actividad técnica y forense para Sentinel. |
| `backups/` | (Próximamente) Copias de seguridad cifradas de la base de datos local. |

---

## 🚀 Requisitos Técnicos

- **Node.js**: Versión 20 (LTS) o superior.
- **SQLite**: No requiere instalación externa (usa `better-sqlite3` embebido).
- **Red**: Recomendamos el uso de **Tailscale** para un acceso remoto seguro sin abrir puertos públicos.
- **Gestor de Paquetes**: `pnpm` o `npm`.

---

## 📡 Arquitectura de Puertos

- **3000**: Gateway Central de Hermes (WebSocket / Webhooks).
- **3001**: API del Command Center para el Panel Nexo OS.
- **5173**: Servidor de desarrollo de la Mini App (React / Vite).
