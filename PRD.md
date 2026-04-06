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
- **Comunicación**: grammY (Telegram Gateway), WebSockets.
- **Base de Datos**: SQLite (better-sqlite3) - 100% Local y persistencia síncrona.
- **Inteligencia**: Motores de inferencia en Groq (Llama 3) y OpenRouter (Claude, GPT-4).
- **Seguridad**: Zero-Trust Implementation, HMAC-SHA256, Sentinel Audit.
- **Frontend**: React (Vite) - Nexo OS v2.0 (Sovereign Terminal).
- **Herramientas**: MCP (Model Context Protocol).

## 🚀 Fases de Desarrollo

### Fase 1: Gateway Base y Motor LLM

- Implementación de servidor WebSocket central.
- Conexión primaria con Telegram y DM Pairing.
- Lógica de failover Groq <> OpenRouter.

### Fase 2: Nodos Locales y Navegador

- Implementación de `system.run` y control de navegador (CDP).
- Carga de habilidades dinámicas.

### Fase 3: Seguridad Cloud (Tailscale)

- Blindaje de red y protección de puertos mediante Tailscale Guard.
- Orquestación de sesiones nativa.

### Fase 4: Audio y Multimedia

- Integración de ElevenLabs para respuesta por voz (TTS).
- Procesamiento de archivos y audio en tiempo real.

### Fase 5: Live Canvas (A2UI) y Automatización

- Dashboard en tiempo real con validación Zod.
- Motor proactivo (CRON) para tareas programadas.

### Fase 6: Zero Trust Desktop Node

- Separación de la lógica de ejecución en un "Nodo de Escritorio" certificado.
- Handshake de seguridad mediante tokens.

### Fase 7: Agente de Calidad Determinista (QA)

- Auditores de seguridad y funcional nativos.
- Diagnóstico inteligente solo ante fallos.

### Fase 8: Sentinel (Security Monitor)

- Monitorización de logs de sistema para detección de ataques.
- Alertas inmediatas en Telegram ante anomalías.

### Fase 9: MCP Integration

- Soporte para herramientas estandarizadas mediante el protocolo de Anthropic (MCP).
- Aduana de seguridad (`allowlist.json`) para herramientas de terceros.

### Fase 10: Nexo Vault (OAuth Manager)

- Almacén local cifrado para el manejo seguro de flujos OAuth de terceros.
- Centralización de secretos y tokens con acceso granular.

### Fase 21: Módulo Hermes (Resiliencia)

- Refactorización total a grammY.
- Gestión de tráfico (Rate limits) y UX fluida con feedback instantáneo.

### Fase 22: El Infiltrado (Navegador Autónomo)

- Orquestación de navegador en modo *headless* para interacción web proactiva.
- Scraping inteligente y automatización de tareas en sitios sin API.

### Fase 23: Memoria Semántica (Cortex Vectorial)

- Integración de SQLite-VSS para búsqueda vectorial local.
- Clasificación semántica de documentos e historial de interacción.

### Fase 24: Nexo DocOps (Trazabilidad)

- Generación dinámica de diagramas arquitectónicos y documentación viva.
- Sincronización automática de hitos y cambios técnicos.

### Fase 25: Bibliotecario & Obsidian RAG

- Integración profunda con el Vault de Obsidian para recuperación de conocimiento.
- Sistema de lectura multinivel y optimización de contexto.

## 📐 Alcance del Sistema

### Incluido

- Orquestación multi-agente.
- Enrutamiento de contexto basado en sobres (`Envelope`).
- Ejecución de comandos en terminal segura.
- Navegación web automatizada (Browser tools).
- Gestión de memoria personal (Long-term memory en SQLite).

### Fuera de Alcance (Por ahora)

- Interfaz móvil nativa (usando PWA o Mini App).
- Entrenamiento de modelos propios (se usan APIs).
