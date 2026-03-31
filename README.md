# 📚 Nexo Documentation: Especificaciones y Plan Maestro

Este repositorio contiene la **documentación técnica central** del ecosistema Nexo. Aquí se definen los requisitos (PRD), planos arquitectónicos (ARQ), planes de ejecución (PLAN) y normativas de seguridad que rigen el desarrollo del asistente.

![Doc Version](https://img.shields.io/badge/Doc-2.2.0-blue?style=for-the-badge)
![Ecosystem](https://img.shields.io/badge/Ecosystem-Nexo-2563EB?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Phase_20_Ready-success?style=for-the-badge)

---

## 🗺️ Mapa de Documentación

Para entender Nexo, navega a través de estos pilares fundamentales:

| Documento | Propósito |
| :--- | :--- |
| **`[[PRD.md]]`** | **Product Requirements Document**: El "qué" y el "para qué" de cada función. |
| **`[[ARQ.md]]`** | **Architecture Specification**: El "cómo" técnico, diagramas y stack. |
| **`[[PLAN.md]]`** | **Master Plan**: Hoja de ruta detallada por fases y entregables. |
| **`[[CHANGELOG.md]]`** | **Historial de Cambios**: Evolución cronológica del sistema de documentación. |
| **`[[SECURITY.md]]`** | **Security Protocols**: Normas Zero-Trust y defensa perimetral. |
| **`[[FUNDAMENTOS.md]]`** | **Core Principles**: Filosofía del proyecto y estandarización. |
| **`[[CONFIG.md]]`** | **Deployment Guide**: Manual de instalación y orquestación. |

---

## 🚀 Fases Actuales en Documentación

Actualmente, la documentación cubre hasta la **Fase 20 (Phalanx)**, detallando la infraestructura de defensa activa:

- **🛡️ Warden (Fase 16)**: Infraestructura y Synology.
- **🕵️ Specter (Fase 19)**: Auditoría Ofensiva / Red Team.
- **⚔️ Phalanx (Fase 20)**: Blue Team / IPS / Firewall nativo macOS.

---

## 🏛️ Estándares de Arquitectura (Nexo Standard)

Toda la documentación sigue el estándar de **Soberanía Digital**:
1. **Local-First**: Prioridad absoluta al procesamiento en el host local.
2. **AI-Agnostic**: Diseñado para operar con cualquier LLM vía failover.
3. **Deterministic First**: Las acciones críticas deben ser verificables mediante código Node.js nativo antes de usar inferencia de IA.

---

*Repositorio de mantenimiento documental para Kike Cid por Antigravity.*
