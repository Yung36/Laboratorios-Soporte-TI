# 📧 Manual de Soporte Microinformático y Aplicaciones Corporativas
Este módulo contiene la documentación técnica de mis prácticas de Mesa de Ayuda (Helpdesk) enfocadas en la resolución de incidentes en la Suite de Microsoft Office 365, clientes de correo y gestión de bases de datos locales indexadas.

## 📋 Laboratorio 2: Troubleshooting ante Bloqueo de Aplicaciones y Corrupción de Caché
**Objetivo:** Diagnosticar y resolver congelamientos en la carga de perfiles y desincronización de datos utilizando la lógica de purga y renombrado seguro de bases de datos del usuario (`AppData`).

### 🔹 Caso A: Pérdida de Sesión en Clientes de Correo ("Desconectado")
* **Origen del problema:** Desconfiguración o expiración del token de seguridad tras un cambio de credenciales en el Active Directory de la empresa.
* **Resolución:** Verificación de conectividad en Capa 3. Posteriormente, interactuar con la barra de estado de la aplicación para invocar el prompt interactivo de Microsoft 365 y refrescar las credenciales corporativas del usuario.

### 🔹 Caso B: Gestión de Cuotas Excedidas ("Buzón Lleno")
* **Origen del problema:** El buzón de almacenamiento en la nube llegó al límite del licenciamiento empresarial (ej. 50 GB), impidiendo el envío y recepción de correos.
* **Resolución:** Creación e implementación de un archivo de datos local **.PST**. Configuración de directivas de autoarchivado para mover elementos con antigüedad mayor a un año hacia el disco duro local, liberando espacio inmediato en la nube sin pérdida de historial.

### 🔹 Caso C: Perfiles Congelados y Corrupción de Base de Datos Local (`.OST` / `.DAT`)
* **Origen del problema:** Fallas lógicas o cierres forzados del sistema que corrompen el archivo de indexación local donde las aplicaciones (como Outlook clásico o servicios nativos de Windows 11) guardan la caché de usuario.
* **Resolución:** Cierre total de procesos desde el Administrador de Tareas. Navegación mediante variables de entorno a las rutas ocultas del sistema (`%localappdata%\Microsoft`). 
* **Técnica de Mitigación Segura (Renombrado):** Aplicación de la regla de soporte: *Nunca borrar de forma permanente a la primera*. Se localiza la base de datos (ej. archivos `.ost` o la estructura `WebCache` con archivos `.dat` y `.log`) y se renombra con la extensión `.viejo` o `.bak`. Al reiniciar la aplicación, el sistema se ve obligado a regenerar un entorno de base de datos totalmente limpio desde la nube, mitigando el error.

---

## 📸 Evidencia del Laboratorio (Estructura de Base de Datos Local)
A continuación se adjunta la captura de la ruta de almacenamiento oculto analizada, donde se aprecian los archivos de logs corporativos (`V01.log`) y el contenedor de base de datos indexada (`.dat`) manipulados para el descarte de corrupción de caché:

![Evidencia de Base de Datos Local]

<img width="634" height="345" alt="2026-10-06_20-01" src="https://github.com/user-attachments/assets/15a60aad-38ca-45d2-b4f1-97ad5a5423dd" />


