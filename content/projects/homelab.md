+++
title = "HomeLab"
date = "2025-02-07"
description = "Una descripcion de mi propio servidor en casa."
tags = ["server", "homelab", "ubuntu-server"]
featured = true
+++

# Problematica
Necesitaba un entorno controlado para simular servicios reales, probar tecnologias, aprender sobre Linux para desplegar un servidor real. 

# Solución
Implementé un servidor central (**Abyss**) bajo ubuntu-server para orquestar servicios mediante contenedores docker.

## Topologia de red.
![Topologia de red dentro de mi hogar](/images/topologia-red.png)

## HomeLab.
![Imagen de los servicios que corre mi homelab](/images/abyss-server.png)

* **OS:** Ubuntu Server
* **Domain Name:** abyss.hollownest.lan
* **Red:** Dominio local `hollownest.lan` gestionado por `pi-hole`
* **Servicios:** 
  * Reverse Proxy - Nginx
  * Monitoreo - UptimeKuma
  * Documentacion - Wiki Js
  * DNS y AdBlock - pi-hole
  * Archivos Compartidos - Samba
  * Firewall - UFW
  * Impresion - CUPS

### Descripción
Para poder utilizar abyss sin preocupaciones la primer barrera es **UFW** para controlar el trafico, esto surge debido a proyectos que necesito correr en un futuro que requieren seguridad. 

Abyss redirecciona el trafico http/https mediante nginx que actua de reverse proxy. En diferentes puertos tengo servicios que me brindan diferentes utilidades.

Por ejemplo algunos servicios que me resultan util: 

* **pi-hole** es el DNS para definir los nombres de dominio y ademas evitar resolver nombres para paginas de publicidad cuando navego por internet.
* **samba** me resulta util para mover archivos entre dispositivos y compartirlo con mis compañeros de piso.
* **UptimeKuma** es un servicio con interfaz web que sirve para monitorear paginas, servicios o hasta los mismos dispositivos de mi red. 

De esta forma cada vez que encuentro o me recomiendan un servicio lo corro en mi homelab, si me resulta util lo dejo corriendo en un puerto, configuro su direccion en nginx y pihole, lo documento y lo uso.
