---
layout: post
title:  "Práctica 15"
date:   2022-03-07 03:32:51 -0600
categories: README
---

# Práctica: Instalación de WordPress usando contenedores Docker y Docker Compose

#### Nombre y Apellidos: Eduardo Saracho Cruz
#### Curso: 2º ASIR - Implantación de aplicaciones web
#### IES Celia Viñas 2021-2022
---
## **Install_docker.sh**
---
## Paso 1
<p style='text-align: justify;'>Definimos la variable de usuario y actualizamos el sistema para evitar posibles errores.</p>

```bash
#!/bin/bash

set -x

# Variables
USER_NAME=ubuntu

# Actualizamos la lista de paquetes
apt update
apt upgrade -y
```
---
## Paso 2
<p style='text-align: justify;'>Descargamos el script de <b>Docker (get-docker.sh)</b> y lo ejecutamos. Seguidamente, añadimos nuestro usuario al grupo docker del sistema.</p>

```bash
# Descargamos el script
curl -fsSL https://get.docker.com -o get-docker.sh

# Ejecutamos el script
sh ./get-docker.sh

# Añadimos nuestro usuario al grupo docker 
usermod -aG docker $USER_NAME
```
---
## Paso 3
<p style='text-align: justify;'>Iniciamos el servicio de <b>Docker</b> y lo configuramos para que inicie automáticamente al iniciar el sistema. Como paso adicional instalaremos <b>Docker-Compose</b>. Es importante actualizar los permisos del grupo docker al finalizar el script con el comando: <b><i>newgrp docker</i></b>.</p>

```bash
# Actualizamos los permisos del grupo docker fuera del script: newgrp docker

# Iniciamos el servicio de docker
systemctl start docker

# Configuramos para que el servicio se inicie automáticamente
systemctl enable docker

# Instalamos docker-compose
apt-get install docker-compose -y
```
---
## **Docker-compose.yml**
---
## Paso 1
<p style='text-align: justify;'>Crearemos un archivo <b>docker-compose.yml</b> para poder desplegar los servicios de <b>WordPress</b>, <b>MySQL</b> y <b>phpMyAdmin</b> utilizando las imágenes oficiales de <b>Docker Hub</b>.</p>
<p style='text-align: justify;'>Utilizará la versión 3.3 y tendrá definidos cuatro servicios diferentes.</p>

![]({{site.url}}/images/wordpress.png)
---

![]({{site.url}}/images/mysql.png)
---

![]({{site.url}}/images/phpmyadmin2.png)
---

![]({{site.url}}/images/https-portal2.png)
<p style='text-align: justify;'>Al final del archivo de <b>docker-compose</b> definiremos los volúmenes de <b>wordpress</b>, <b>mysql</b> y <b>https-portal</b> junto a las redes de <b>frontend</b> y <b>backend</b>.</p>
![]({{site.url}}/images/volumes-networks2.png)
