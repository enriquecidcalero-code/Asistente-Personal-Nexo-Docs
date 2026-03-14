# 🌌 Nexo (Open Gravity) - Documentación Central

> **El plano de control central para tu asistente personal de IA soberano.**

Bienvenido al repositorio oficial de documentación del **Asistente Personal Nexo (Open Gravity)**. Este proyecto es un sistema de orquestación de IA avanzado, diseñado para ejecutarse localmente proporcionando máxima privacidad, control y una arquitectura de confianza cero.

## 🎯 ¿Qué es Nexo?

Nexo es un **Gateway (Pasarela)** inteligente que unifica múltiples canales de comunicación (Telegram, WebSockets), motores de inteligencia artificial (Groq, OpenRouter) y herramientas del sistema local en una única interfaz cohesiva.

### Pilares Fundamentales
- **Privacidad Total**: Procesamiento local-first y cifrado de datos.
- **Resiliencia**: Sistema de failover automático entre proveedores de LLM.
- **Confianza Cero (Zero Trust)**: Handshake certificado entre nodos y gateway.
- **Modularidad**: Habilidades y herramientas cargables dinámicamente.

---

## 🗺️ Guía de Documentación

Para entender cómo funciona Nexo y qué hemos construido hasta ahora, te recomendamos seguir este orden:

1. [**📋 PRD (Requisitos)**](PRD.md): Definición del producto, objetivos y visión.
2. [**🏗️ Arquitectura**](ARQ.md): Diagramas técnicos y stack tecnológico.
3. [**📅 Plan Maestro**](PLAN.md): Roadmap de fases y estado actual.
4. [**🔐 Seguridad**](SECURITY.md): Detalles del sistema Sentinel, Pairing y protección de nodo.
5. [**📜 Changelog**](CHANGELOG.md): Historial detallado de todas las versiones y mejores implementadas.

---

## 🚀 Estado Actual: Fase 9 (MCP)

Actualmente, Nexo se encuentra en su **Fase 9**, lo que significa que ya es capaz de:
- [x] Gestión de seguridad via **Sentinel** con alertas proactivas.
- [x] Integración de **MCP (Model Context Protocol)** para usar herramientas externas.
- [x] Control de **Desktop Node** certificado.
- [x] Interfaz de visualización **Live Canvas**.
- [x] Comunicación bidireccional segura por **Telegram**.

---

## 🛠️ Configuración Rápida (Overview)

Nexo utiliza un sistema de persistencia local en `~/.nexo/` que contiene:
- `workspace/`: Sesiones, allowlist y configuración.
- `logs/`: Auditoría forense detallada.
- `security/`: Certificados y tokens de seguridad.

---

*Documentación redactada por Antigravity (IA).*
