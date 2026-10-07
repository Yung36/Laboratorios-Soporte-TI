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

# 🎫 Manual de Gestión de Incidentes y Operaciones de Mesa de Ayuda (ITIL Framework)
Este módulo contiene la documentación técnica de mis laboratorios prácticos orientados a la administración de colas de trabajo, priorización de incidentes y cumplimiento de Acuerdos de Nivel de Servicio (SLA) utilizando la herramienta empresarial estándar de la industria: **Jira Service Management**.

## 📋 Laboratorio 4.1: Configuración de Mesa de Ayuda y Ciclo de Vida del Ticket
**Objetivo:** Aplicar el marco de trabajo ITIL para clasificar, asignar, diagnosticar y cerrar de forma exitosa un Incidente Mayor en la plataforma Jira, incluyendo la administración avanzada del motor de resoluciones del sistema.

### ⚙️ 1. Clasificación Operativa del Incidente (Matriz de Prioridad)
Ante una cola simultánea de solicitudes en el entorno de producción, se analizó el caso crítico bajo las variables de **Urgencia** (detención del servicio) e **Impacto** (afectación al negocio):
* **Código de Ticket:** `IT-1`
* **Resumen:** Falla Crítica: Pantallazo Azul (BSOD) en estación de facturación de Recepción.
* **Diagnóstico Inicial:** Impacto masivo en la recaudación de caja presencial con 10 clientes en fila de espera. Se clasifica como **Prioridad Alta / Crítica** con un SLA de respuesta inmediata (<30 minutos).

### 🔄 2. Flujo de Trabajo Ejecutado (Workflow en Jira)
Para mantener la gobernanza y la trazabilidad del incidente, se operaron las siguientes transiciones de estado en la plataforma:
1. **Apertura y Adjudicación:** Se toma propiedad del incidente mediante la directiva `Assignee -> Assign to me` para registrar al técnico responsable.
2. **Inicio de Operaciones:** Transición de estado de `Open` a **`Work in progress`**, notificando formalmente al negocio el inicio del proceso de soporte técnico en sitio.

---

## 📸 Evidencia 01: Ticket Asignado y En Progreso
A continuación se documenta el panel de control de Jira con el incidente adjudicado correctamente a mi perfil técnico y el workflow activo en estado de ejecución:

Ticket En Progreso

<img width="1240" height="520" alt="2026-10-07_16-34" src="https://github.com/user-attachments/assets/100733e2-f888-4144-aa9d-95807313af21" />

---

### 🛠️ 3. Solución Técnica Aplicada e Inyección de Resoluciones
Una vez asistido el usuario en sitio se ejecutó el siguiente protocolo:
1. **Plan de Contingencia:** Se migró temporalmente la operación de la recepcionista a una estación de trabajo secundaria libre para liberar el flujo de clientes y mitigar el impacto financiero del negocio.
2. **Troubleshooting de Sistema:** Se forzó el reinicio de la máquina afectada en el *Entorno de Recuperación de Windows 11*, detectando corrupción lógica de controladores posterior a una actualización automatizada. Se desinstaló exitosamente el último paquete de actualización de calidad, restableciendo el booteo normal del sistema operativo al 100%.
3. **Administración del Core de Jira (Resoluciones):** Al encontrarse la plataforma en estado base, se accedió al menú de administración global (`Jira Admin Settings -> Work items -> Resolutions`) para inyectar de forma manual el atributo de cierre **`Done`** (Hecho) en el motor del software.
4. **Cierre Formal:** Se aplicó la transición de estado final a **`Completed / Done`** registrando la nota técnica en el historial histórico de la infraestructura para futuras auditorías.

---

## 📸 Evidencia 02: Cierre Exitoso e Historial Archivador
Captura final de la Mesa de Ayuda que confirma la resolución exitosa del incidente `IT-1` con el estado actualizado en verde (`Completed`), listo para la auditoría de métricas del supervisor de TI:

Ticket Completado

<img width="1268" height="558" alt="2026-10-07_16-34_1" src="https://github.com/user-attachments/assets/043a97cd-a0fe-4940-9cfb-b3d6c5af8247" />


