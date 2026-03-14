# 🌌 Nexo (Open Gravity) - Documentación Central

> **El plano de control central para tu asistente personal de IA soberano.**

Bienvenido al repositorio oficial de documentación del **Asistente Personal Nexo (Open Gravity)**. Este proyecto es un sistema de orquestación de IA avanzado, diseñado para ejecutarse localmente proporcionando máxima privacidad, control y una arquitectura de confianza cero.

---

## 🛡️ Filosofía de Desarrollo: Seguridad Total por Diseño

A diferencia de otros asistentes que priorizan la funcionalidad y luego intentan "parchear" la seguridad, Nexo ha sido construido con una **mentalidad de Fortificado Progresivo**.

Nuestra base estratégica ha sido:
1.  **Restricción Total (Fase 1)**: Comenzar en un entorno completamente sellado donde nada puede entrar ni salir sin autorización explícita (DM Pairing).
2.  **Base Robusta**: Crear un núcleo (Gateway) que no confía en nadie, ni siquiera en el nodo que ejecuta los comandos.
3.  **Apertura Controlada**: A medida que añadimos habilidades (Navegación, Audio, MCP), cada una pasa por una "aduana" de seguridad (Sentinel, Allowlists, Zod Validation) para asegurar que el sistema nunca pierda su integridad.

---

## 🚀 Análisis Detallado de Fases

Nexo ha evolucionado a través de 9 fases críticas, cada una añadiendo una capa de blindaje:

### [Fase 1-2] El Sistema Nervioso y el Perímetro
*   **Seguridad**: Implementación del **DM Pairing**. El sistema protege el acceso mediante un código físico generado localmente.
*   **Impacto**: Blindaje total contra extraños desde el primer minuto.

### [Fase 3-4] Aislamiento de Red y Memoria
*   **Seguridad**: Integración de **Tailscale Network Guard**. Nexo solo escucha en interfaces seguras y detecta exposiciones accidentales.
*   **Impacto**: Invisibilidad en la red pública mientras se mantiene acceso remoto seguro.

### [Fase 6-7] Confianza Cero (Zero Trust) y Auditoría
*   **Seguridad**: Creación del **Desktop Node**. Desacoplamos la ejecución del Gateway. El nodo intercepta comandos peligrosos (`sudo`, `rm`) mediante un motor de reglas nativo.
*   **Impacto**: Separación física y lógica entre la "inteligencia" y la "ejecución de comandos".

### [Fase 8-9] Vigilancia Proactiva y Aduana de Herramientas (MCP)
*   **Seguridad**: El módulo **Sentinel** escanea logs forenses en tiempo real y la **Aduana MCP** permite/deniega el uso de herramientas externas.
*   **Impacto**: Control total y monitorización pasiva 24/7 de cada acción del sistema.

---

## 🗺️ Guía de Documentación

1. [**📋 PRD (Requisitos)**](PRD.md): Definición detallada, objetivos y visión del producto.
2. [**🏗️ Arquitectura**](ARQ.md): Diagramas técnicos y stack tecnológico (Node/TS/pnpm).
3. [**🧠 Fundamentos Técnicos**](FUNDAMENTOS.md): **[NUEVO]** Explicación profunda de la ingeniería: Gateway, Motores LLM, Failover y Lógica de Nodos.
4. [**📅 Plan Maestro**](PLAN.md): Roadmap histórico y próximos hitos del proyecto.
5. [**🔐 Seguridad**](SECURITY.md): El manual profundo de Sentinel, Node Protection y Pairing.
6. [**📜 Changelog**](CHANGELOG.md): Historial de versiones y mejoras implementadas.

---

*Documentación mantenida y evolucionada por Antigravity (IA).*
