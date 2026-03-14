# 📅 Plan Maestro y Roadmap: Evolución Segura de Nexo

Este documento detalla la hoja de ruta estratégica de Nexo, enfocándose en cómo cada hito ha sido diseñado para expandir las capacidades del asistente sin comprometer la seguridad del sistema local.

---

## 🛡️ Filosofía: De la Restricción a la Apertura Controlada

Nexo no es un "producto terminado", es una **evolución de seguridad**. Nuestra metodología consiste en cerrar todas las puertas por defecto y solo abrir aquellas que cuentan con un sistema de monitorización activo.

---

## ✅ Hitos Alcanzados: El Camino de la Seguridad

### [Fase 1-2] Los Cimientos del Bunker
*   **Hitos**: Creación del Gateway WebSocket, Motor LLM con Failover y Módulo Telegram.
*   **Enfoque de Seguridad**: El sistema nace "ciego y sordo" para el mundo exterior. Solo responde a través de un **Apretón de Manos (Pairing)** validado localmente.
*   **Estado**: 100% Funcional.

### [Fase 3-4] El Blindaje de Red y Multimodalidad
*   **Hitos**: Integración de **Tailscale**, enrutamiento de sesiones y audio TTS.
*   **Enfoque de Seguridad**: Se implementa el **Network Guard** que bloquea el sistema si detecta una IP pública no autorizada. El audio se maneja en flujos aislados para evitar fugas de datos.
*   **Estado**: 100% Funcional.

### [Fase 5] El Espejo Seguro (A2UI)
*   **Hitos**: Dashboard **Live Canvas** y motor proactivo (CRON).
*   **Enfoque de Seguridad**: Introducción de esquemas **Zod**. Ningún dato puede pintarse en el canvas ni ningún comando puede ser enviado desde él si no cumple con el contrato de integridad definido.
*   **Estado**: 100% Funcional.

### [Fase 6-7] La Delegación de Confianza (Zero Trust)
*   **Hitos**: **Desktop Node** certificado y **Agente de QA** Determinista.
*   **Enfoque de Seguridad**: Este es el mayor salto. Separamos la "mente" (Gateway) del "brazo" (Nodo). El brazo tiene su propio cerebro de seguridad que bloquea proactivamente comandos de terminal sensibles (`rm`, `sudo`, `mv`). El Agente de QA audita el entorno cada 60 segundos buscando brechas.
*   **Estado**: 100% Funcional.

### [Fase 8] El Ojo que todo lo ve (Sentinel)
*   **Hitos**: Sistema Sentinel y Alertas de Telegram.
*   **Enfoque de Seguridad**: **Seguridad Pasiva**. Un guardián que analiza los logs forenses buscando patrones de ataque u ofuscación, alertando al usuario al instante.
*   **Estado**: 100% Funcional.

### [Fase 9] La Aduana Universal (MCP)
*   **Hitos**: Cliente MCP Seguro y Aduana de Herramientas.
*   **Enfoque de Seguridad**: Las herramientas externas son inherentemente peligrosas. Hemos creado una **Aduana Digital** (`mcp_allowlist.json`). Si una herramienta no está pre-aprobada por el humano, la IA no puede usarla, por muy persuasiva que sea.
*   **Estado**: fase actual completa.

---

## 🚧 Próximos Pasos: Inteligencia con Seguridad Vectorial

### Fase 10: Memoria a Largo Plazo Sometida a Auditoría
*   [ ] Integración de Base de Datos Vectorial local.
*   [ ] Indexación de archivos con permisos granulares (Solo carpetas autorizadas).
*   [ ] Auditoría de "olvido" (GDPR local).

### Fase 11: Ecosistema Móvil Certificado
*   [ ] Extensión del modelo Zero Trust a dispositivos Android/iOS.
*   [ ] Geocerca de seguridad (El asistente se bloquea si el móvil sale de un perímetro).

### Fase 12: Nube Híbrida Zero-Knowledge
*   [ ] Sincronización con Firebase usando cifrado de extremo a extremo (E2EE), donde solo el usuario tiene la llave.

---

## 📈 Métricas de Robustez
*   **Surface Attack**: Reducida al mínimo mediante Tailscale.
*   **Command Isolation**: 100% (Intercepción en Nodo Desktop).
*   **Tool Authorization**: Manual y Determinista (Aduana MCP).
