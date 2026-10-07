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
