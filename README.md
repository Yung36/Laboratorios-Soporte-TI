# 🌐 Manual de Diagnóstico de Redes (Capa 1 a Capa 3)
Este módulo contiene la documentación técnica y las evidencias de mis prácticas de soporte de conectividad y operaciones de red (NOC).

## 📋 Laboratorio 1: Troubleshooting ante Caída de Conectividad Base
**Objetivo:** Diagnosticar la pérdida de acceso a servicios o internet en una estación de trabajo Windows 11 aplicando el modelo OSI de abajo hacia arriba y comandos nativos del CMD.

### 🔹 1. Análisis del Adaptador Local (`ipconfig /all`)
Al ejecutar el comando, se extraen los valores lógicos esenciales de la tarjeta de red física (Realtek PCIe GbE):
* **DHCP Habilitado (Sí):** Confirma que el enrutador asigna la configuración automáticamente.
* **Dirección IPv4 (`192.168.1.84`):** Identidad lógica de la máquina en la LAN. *(Nota de soporte: Si mostrara una IP `169.254.X.X`, indica una falla de asignación del servidor DHCP / APIPA).*
* **Puerta de Enlace Predeterminada (`192.168.1.1`):** IP local del Router físico de la empresa.
* **Servidores DNS (`1.1.1.1` / `1.0.0.1`):** Encargados de la resolución de nombres de dominio.

### 🔹 2. Prueba de Enlace Local (`ping 192.168.1.1`)
Prueba ICMP directa hacia la puerta de enlace para descartar fallas en las capas físicas y de enlace (Capa 1 y Capa 2):
* **Resultado:** 0% de paquetes perdidos y latencia `<1ms`. Confirma que el cable Ethernet, el puerto del switch y el protocolo Spanning Tree (STP) operan correctamente sin bucles físicos en la infraestructura.

### 🔹 3. Análisis de Enrutamiento Externo y Saltos (`ping 8.8.8.8`)
Verificación de la salida hacia el exterior (Internet) utilizando el DNS público de Google:
* **Análisis del TTL:** El contador finalizó en `117`. Tomando en cuenta un TTL inicial estándar de servidor de `128`, se determina mediante lógica aplicada que el tráfico transitó exitosamente a través de **11 saltos de routers intermedios** (nodos de proveedores locales e internacionales) antes de retornar.

---

## 📸 Evidencia del Laboratorio (CMD de Windows)
A continuación se adjunta la captura de pantalla de las pruebas ejecutadas en la terminal de comandos de Windows 11:

<img width="520" height="448" alt="2026-10-05_16-44" src="https://github.com/user-attachments/assets/542bf304-47d4-474f-9efb-a3f9cc04f2a4" />



