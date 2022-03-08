---
layout: post
title:  "Práctica 16"
date:   2022-03-07 03:32:51 -0600
categories: README
---

# Práctica: Instalación de PrestaShop usando contenedores Docker y Docker Compose

#### Nombre y Apellidos: Eduardo Saracho Cruz
#### Curso: 2º ASIR - Implantación de aplicaciones web
#### IES Celia Viñas 2021-2022
---
## **Docker-compose.yml**
---
## Paso 1
<p style='text-align: justify;'>Crearemos un archivo <b>docker-compose.yml</b> para poder desplegar los servicios de <b>Prestashop</b>, <b>MariaDB</b> y <b>phpMyAdmin</b> utilizando las imágenes oficiales de <b>Docker Hub</b>. La imágen de <b>Prestashop</b> que se utilizará, sera la de <b>Bitnami</b>.</p>
<p style='text-align: justify;'>Utilizará la versión 3.3 y tendrá definidos cuatro servicios diferentes.</p>

![]({{site.url}}/images/prestashop.png)
---

![]({{site.url}}/images/mariadb.png)
---

![]({{site.url}}/images/phpmyadmin.png)
---

![]({{site.url}}/images/https-portal.png)
<p style='text-align: justify;'>Al final del archivo de <b>docker-compose</b> definiremos los volúmenes de <b>prestashop</b>, <b>mariadb</b> y <b>https-portal</b> junto a las redes de <b>frontend</b> y <b>backend</b>.</p>
![]({{site.url}}/images/volumes-network.png)

---
## **.env**
---
## Paso 1
<p style='text-align: justify;'>Definiremos en un fichero <b>.env</b> todas las variables que utilizará el archivo <b>docker-compose.yml</b>.</p>

```bash
# Configuración de acceso a la base de datos
MYSQL_ROOT_PASSWORD=password
MYSQL_DATABASE=prestashop_db
MYSQL_USER=prestashop_user
MYSQL_PASSWORD=prestashop_password

# Configuración de PrestaShop
PRESTASHOP_FIRST_NAME=Usuario
PRESTASHOP_LAST_NAME=Apellido
PRESTASHOP_PASSWORD=admin_password
PRESTASHOP_EMAIL=admin@mail.es
PRESTASHOP_HOST=practica16iaw.ddns.net
PRESTASHOP_ENABLE_HTTPS=yes
PRESTASHOP_COUNTRY=es
PRESTASHOP_LANGUAGE=es
PRESTASHOP_DATABASE_HOST=mariadb
```
