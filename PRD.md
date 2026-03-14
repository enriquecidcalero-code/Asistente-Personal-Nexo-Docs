# 📋 Documento de Requisitos del Producto (PRD)

## 🌌 Visión General
Nexo (Open Gravity) es un asistente de IA personal **local-first** diseñado para la máxima privacidad, control y extensibilidad. Actúa como un plano de control central (Gateway) que orquesta múltiples agentes, herramientas locales y canales de comunicación.

## 🎯 Objetivos Estratégicos
1. **Soberanía de Datos**: Que el usuario sea el único dueño de su historial y logs.
2. **Resiliencia Operativa**: Funcionar incluso si un proveedor de IA (como Groq) tiene una caída.
3. **Escalabilidad Modular**: Capacidad de añadir "Habilidades" (Skills) sin modificar el núcleo del sistema.
4. **Seguridad Proactiva**: Sistema Sentinel que monitorea y bloquea amenazas en tiempo real.

## 🛠️ Stack Tecnológico
- **Core**: Node.js v20+, TypeScript.
- **Comunicación**: WebSockets (ws), Telegram Bot API.
- **Inteligencia**: Motores de inferencia en Groq (Llama 3) y OpenRouter (Claude, GPT-4).
- **Seguridad**: Zod (Validación), Regex-based Sentinel.
- **Herramientas**: MCP (Model Context Protocol) para integraciones externas.

## 🚀 Fases de Desarrollo

### Fase 1: Gateway y Audio
- Implementación de servidor WebSocket central.
- Integración de ElevenLabs para respuesta por voz (TTS).
- Conexión primaria con Telegram.

### Fase 2: Automatización y Contexto
- Implementación de motor de sesiones persistentes.
- Sistema de failover automático entre Groq y OpenRouter.

### Fase 3: Live Canvas (A2UI)
- Creación de un Dashboard en tiempo real que reacciona a los comandos de la IA.
- Visualización de datos dinámica.

### Fase 4: Zero Trust Node
- Separación de la lógica de ejecución en un "Nodo de Escritorio" certificado.
- Handshake de seguridad mediante tokens.

### Fase 5: Sentinel (Security Monitor)
- Monitorización de logs de sistema para detección de ataques.
- Alertas inmediatas en Telegram ante anomalías.

### Fase 6: MCP Integration (Fase Actual)
- Soporte para herramientas estandarizadas mediante el protocolo de Anthropic (MCP).
- Allowlist de herramientas seguras.

## 📐 Alcance del Sistema
### Incluido:
- Orquestación multi-agente.
- Ejecución de comandos en terminal segura.
- Navegación web automatizada (Browser tools).
- Gestión de memoria personal (Long-term memory).

### Fuera de Alcance (Por ahora):
- Interfaz móvil nativa (solo Telegram/Web).
- Entrenamiento de modelos propios (se usan APIs).
