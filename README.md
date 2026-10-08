# 🌐 Manual de Herramientas de Diagnóstico de Redes y Operaciones del NOC
Este módulo contiene la documentación técnica y las evidencias de mis prácticas avanzadas en la consola de comandos de Windows (CMD), orientadas al monitoreo de infraestructura de red y análisis de rutas de tránsito internacional para Operaciones de Red (NOC).

## 📋 Laboratorio 5.1: Análisis de Enrutamiento y Trazabilidad de Rutas (`tracert`)
**Objetivo:** Rastrear el flujo de paquetes de datos desde la red de área local (LAN) residencial hasta un nodo de red de distribución de contenido (CDN) internacional, interpretando variaciones de latencia e identificando políticas de seguridad ICMP en tránsito.

### ⚙️ Interpretación Técnica del Análisis de Trazabilidad Realizado:
Al ejecutar el comando `tracert atlassian.com` hacia la infraestructura de producción del servidor de destino, se extrajo la siguiente matriz de saltos de red lónicos:

1. **Salto 01 (Gateway Local - `192.168.1.1`):** Conectividad inmediata con el enrutador físico perimetral local (LAN). Latencia óptima inferior a `<1ms`, confirmando la estabilidad del canal base de Capa 1 y Capa 2.
2. **Salto 02 (Nodo del ISP - `10.51.32.1`):** Tránsito exitoso hacia la red de agregación del proveedor de internet local mediante enrutamiento privado.
3. **Saltos 03, 04, 05 (Políticas de Seguridad Drop ICMP):** La presencia de asteriscos (`*`) y respuestas de tiempo de espera agotado indican routers troncales con directivas de ciberseguridad activadas (Firewall Drop Rules). Los equipos procesan el paquete pero mitigan el riesgo de escaneo bloqueando respuestas ICMP Echo Reply sin interrumpir el flujo.
4. **Salto 06 (Tránsito Internacional Inter-AS - `mia-b2-link.ip.twelve99.net`):** El paquete cruza el canal internacional de fibra óptica submarina tocando tierra en el punto de presencia (PoP) de **Miami, Florida (EE. UU.)** gestionado por el sistema autónomo de *Arelion*. El salto cuantitativo de latencia a **45ms** valida científicamente el factor físico de distancia y el retardo de propagación a través de la red WAN.
5. **Salto 12 (Destino Final - `cloudfront.net` / `54.240.184.21`):** Conclusión de la traza de forma exitosa en el clúster de servidores perimetrales de Amazon Web Services (AWS / Cloudfront) en la región norteamericana, con una latencia total de **59ms**.

---

## 📸 Evidencia del Laboratorio (Análisis de Tránsito WAN)
A continuación se adjunta el registro del análisis procedimental ejecutado desde la terminal de comandos del sistema:

![Evidencia de Tracert](tracert_evidencia.png)
