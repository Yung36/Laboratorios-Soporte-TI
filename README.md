# 👥 Manual de Gestión de Identidades y Accesos (Active Directory)
Este módulo contiene la documentación técnica de mis laboratorios prácticos orientados a la administración de identidades, control de seguridad centralizado y operaciones de acceso en entornos empresariales mediante Active Directory Domain Services (AD DS).

## 📋 Laboratorio 3.1: Restablecimiento de Contraseñas y Desbloqueo de Cuentas Corporativas
**Objetivo:** Resolver de manera eficiente y segura los incidentes de bloqueo de acceso de los colaboradores (Ticket Nivel 1 más concurrente) utilizando la consola gráfica de Usuarios y Equipos de Active Directory.

### 🔹 Procedimiento Operativo Estándar (SOP):
1. **Identificación del Objeto de Usuario:** Apertura de la consola de administración de AD y ejecución del motor de búsqueda avanzada (`Ctrl + F`) localizando el registro del colaborador mediante su identificador o nombre legal.
2. **Auditoría de Estado y Desbloqueo:** Acceso a las *Propiedades* del usuario, específicamente en la pestaña **Cuenta**. Verificación del check de bloqueo activado por políticas de seguridad del dominio (tras exceder los intentos fallidos permitidos). Marcado de la casilla **"Desbloquear cuenta"** y aplicación de cambios en caliente.
3. **Restablecimiento de Credenciales Seguro (Password Reset):** En caso de olvido de credenciales, se procede a la asignación de una contraseña temporal alfanumérica y compleja.
4. **Directiva de Ciberseguridad Aplicada:** Activación obligatoria de la casilla **"El usuario debe cambiar la contraseña en el siguiente inicio de sesión"**. Esto garantiza el principio de no repudio, asegurando que el técnico de soporte no conozca la contraseña final y privada del colaborador.

### 🚨 Guía de Diagnóstico Avanzado ante "Bloqueos Fantasma" (Troubleshooting de Red)
Si tras aplicar el desbloqueo exitoso en el servidor central de Active Directory, el sistema operativo local del usuario insiste en que la cuenta continúa bloqueada, se aplica la siguiente matriz de descarte técnico:

* **Escenario de Pérdida de Conectividad (Teletrabajo):** Si el colaborador se encuentra remoto, la máquina local retiene el estado de bloqueo en la caché debido a que la sesión no se ha iniciado y, por ende, el túnel **VPN** no se ha establecido. Al no haber comunicación en Capa 3 con los Controladores de Dominio (DC), la computadora no puede sincronizar el nuevo estado.
* **Mitigación de Soporte:** Forzar el levantamiento del agente VPN de la empresa desde la pantalla de bloqueo de Windows utilizando las credenciales temporales, u obligar a una reconexión física a la red LAN corporativa para restablecer el canal seguro de comunicación de identidades.



## 📋 Laboratorio 3.2: Gestión del Ciclo de Vida del Usuario (Onboarding & Offboarding)
**Objetivo:** Documentar los procedimientos operativos estándar para el alta de nuevo personal y la baja segura de colaboradores, aplicando principios de ciberseguridad y continuidad del negocio.

### ➕ Proceso de Alta de Personal (Onboarding)
* **Escenario:** Recursos Humanos solicita la creación de accesos para un nuevo colaborador en un departamento existente.
* **Procedimiento Operativo:** Para optimizar tiempos y garantizar la consistencia de permisos, se aplica la técnica de **Clonación de Perfil**. Se localiza a un usuario activo del mismo departamento, se selecciona la opción `Copiar (Copy)` en Active Directory y se introducen los datos de la nueva identidad (`Nombre`, `Apellido`, `User Logon Name`). Esto hereda de forma automática las membresías a grupos de seguridad y accesos a recursos compartidos en red correspondientes, eliminando el error humano.

### ❌ Proceso de Baja de Personal (Offboarding) y Protocolo de Seguridad
* **Escenario:** Desvinculación inmediata de un colaborador por motivos de seguridad o cese de funciones.
* **Procedimiento Operativo:** 
  1. **NUNCA eliminar el objeto de usuario** en Active Directory para evitar la pérdida de trazabilidad e historiales en el servidor de archivos.
  2. Ejecutar de forma inmediata la directiva **`Deshabilitar cuenta (Disable Account)`**, cortando cualquier sesión activa en caliente.
  3. Realizar un restablecimiento forzado de contraseña (Password Reset) asignando una clave compleja aleatoria y desconocida.
  4. Mover el objeto de usuario a la Unidad Organizativa (OU) de seguridad destinada a `Ex-empleados / Cuentas Inactivas`.

### 🛡️ Delegación Segura de Buzones Históricos (Gobernanza de Datos)
* **Requerimiento:** El supervisor del departamento solicita acceso a la información histórica del correo del ex-empleado.
* **Resolución Técnica en Office 365:** Para mitigar riesgos de suplantación de identidad y cumplir con el principio de *No Repudio*, queda estrictamente prohibido entregar credenciales del ex-empleado a terceros. 
* **Acción:** Se accede al Centro de Administración de Exchange y se transforma el buzón a un **Buzón Compartido (Shared Mailbox)**. Posteriormente, se delegan permisos de `Acceso Completo (Full Access)` al supervisor mediante su propia identidad corporativa. El recurso se monta automáticamente en el cliente Outlook del jefe directo, garantizando la auditoría y la seguridad del proceso.

