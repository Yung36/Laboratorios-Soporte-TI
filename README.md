# 🎫 Manual de Gestión de Incidentes y Operaciones de Mesa de Ayuda (ITIL Framework)
Este módulo contiene la documentación técnica de mis laboratorios prácticos orientados a la administración de colas de trabajo, priorización de incidentes y cumplimiento de Acuerdos de Nivel de Servicio (SLA) utilizando las mejores prácticas de la industria (Framework ITIL).

## 📋 Laboratorio 4.1: Priorización Lógica de Incidentes y Gestión de SLAs
**Objetivo:** Aplicar la matriz de priorización corporativa (Urgencia vs. Impacto) para clasificar y resolver de manera eficiente una cola de incidentes en entornos de alta demanda, minimizando el impacto financiero y garantizando la continuidad operativa del negocio.

### ⚙️ Criterios de Clasificación Operativa:
* **Impacto:** Determina el alcance del incidente (¿Afecta a un usuario individual, a un departamento crítico o a la infraestructura global de la organización?).
* **Urgencia:** Mide el tiempo de degradación del servicio o la detención total de las funciones comerciales del colaborador afectado.

---

### 🚨 Caso de Estudio: Gestión de Cola de Tickets (Simulación Real de Operaciones)

Ante una cola simultánea de solicitudes asignadas en el sistema de tickets (Jira Service Management / ServiceNow), se ejecutó el siguiente orden de atención basado en lógica de negocio:

#### 🥇 1. Prioridad: CRÍTICA (SLA: 30 min - 1 hora)
* **Incidente:** Estación de trabajo principal de cobros en estado de Pantalla Azul (BSOD) con detención total del flujo de facturación presencial.
* **Justificación de Soporte:** Impacto directo en la recaudación de ingresos y afectación al cliente final. Al no existir un mecanismo de contingencia local, se clasifica como *Incidente Mayor* requiriendo Troubleshooting de hardware/sistema inmediato.

#### 🥈 2. Prioridad: MEDIA (SLA: 4 - 8 horas)
* **Incidente:** Falla de impresión a color en periférico privado de Jefatura de Finanzas.
* **Justificación de Soporte:** Urgencia mitigada debido a la existencia de un plan de continuidad funcional alterno (impresión compartida en blanco y negro vía LAN en pasillo). El flujo de trabajo del usuario no está detenido, permitiendo agendar la atención de forma programada dentro del turno diario.

#### 🥉 3. Prioridad: BAJA / REQUERIMIENTO (SLA: 24 - 48 horas)
* **Incidente:** Solicitud de aprovisionamiento de accesos (Onboarding en Active Directory) para colaborador de reingreso programado para la siguiente semana de operaciones.
* **Justificación de Soporte:** No representa una degradación de servicio activa ni detención de funciones en tiempo real. Se gestiona bajo el flujo estándar de solicitudes de requerimiento de TI dentro de la ventana de tiempo contractual del SLA.

