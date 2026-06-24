# Actividad Docker - DAD

### Alumna: Tiziana Yazmin Ochoa

### Materia: Diseño y Arquitectura de Despliegues

### Fecha: 05/05/2026

---

# Objetivo

Implementar los ejemplos del repositorio Docker Tutorial, realizando la construcción de imágenes, ejecución de contenedores, edición de archivos dentro de Docker y conexión desde Visual Studio Code. El desarrollo de todos los ejemplos se encuentran en este Readme.

Repositorio utilizado:

https://github.com/joseluisgs/docker-tutorial

---

# Ejemplo 01 - Edición dentro del contenedor Docker

## Construcción de la imagen

Se construyó la imagen Docker utilizando el archivo Dockerfile del proyecto.

Comando utilizado:

```bash
docker build -t ejem01 .
```

### Captura 1 - Construcción de la imagen

![Construcción de la imagen](Capturas-ejem01/build.jpg)

---

## Verificación de la imagen creada

Se verificó que la imagen estuviera disponible localmente.

Comando utilizado:

```bash
docker images
```

### Captura 2 - Imagen creada

![Imagen creada](Capturas-ejem01/docker-images.jpg)

---

## Ejecución del contenedor

Se ejecutó el contenedor asociado a la imagen creada.

Comando utilizado:

```bash
docker ps
```

### Captura 3 - Contenedor en ejecución

![Contenedor en ejecución](Capturas-ejem01/docker-ps.jpg)

---

## Acceso al contenedor

Se ingresó al contenedor para trabajar directamente sobre el sistema Linux interno.

Comando utilizado:

```bash
docker exec -it ejem01-container bash
```

## Edición del archivo index.html

Se editó el archivo index.html para agregar información personal solicitada por la actividad.

Comando utilizado:

```bash
vi index.html
```

Contenido agregado:

* Nombre: Tiziana Yazmin Ochoa
* Fecha: 05/05/2026
* Materia: Diseño y Arquitectura de Despliegues

### Captura 5 - Edición del archivo

![Edición de indez](Capturas-ejem01/index-html.jpg)

---
## Instalación y verificación de Vim

Una vez dentro del contenedor, se instaló el editor de texto Vim para poder editar archivos desde la terminal Linux.

Comandos utilizados:

```bash
apt-get update
apt-get install -y vim
```

Posteriormente se verificó la correcta instalación mediante:

```
vim --version
```

### Captura 6 - Version de Vim

![Version de Vim](Capturas-ejem01/vim-version.jpg)
![Version de Vim](Capturas-ejem01/vim-version-2.jpg)

---
## Resultado Final

Se verificó el correcto funcionamiento accediendo desde el navegador al servicio publicado por Docker.

URL utilizada:

```text
http://localhost:8080
```

### Captura 7 - Página funcionando

![Página funcionando](Capturas-ejem01/localhost.jpg)

---

## Conexión desde Visual Studio Code

Se instaló la extensión Remote Explorer para conectarse al contenedor Docker desde Visual Studio Code.

### Captura 8 - VS Code conectado al contenedor

![Conteiner en VS code](Capturas-ejem01/vscode-conteiner.jpg)

---

# Ejemplo 02 - Despliegue de WordPress y MariaDB

## Análisis del archivo run.sh

Se analizó el contenido del archivo `run.sh`, el cual automatiza la creación de dos contenedores Docker:

- Un contenedor de base de datos MariaDB.
- Un contenedor WordPress conectado a la base de datos.

### Captura 1 - Contenido de run.sh

![Contenido de run.sh](Capturas-ejem02/runsh-contenido.jpg)

---

## Creación manual del contenedor de base de datos

En lugar de ejecutar el script completo, se ejecutaron manualmente los comandos desde la terminal de Visual Studio Code.

Comando utilizado:

```bash
docker run -d --name wordpress-db --mount source=wordpress-db,target=/var/lib/mysql -e MYSQL_ROOT_PASSWORD=secret -e MYSQL_DATABASE=wordpress -e MYSQL_USER=manager -e MYSQL_PASSWORD=secret mariadb:10.3.9
```

Este contenedor almacena la base de datos utilizada por WordPress.

## Captura 2 - Creación del contenedor MariaDB

![Creación del contenedor MariaDB](Capturas-ejem02/container-mariadb.jpg)

---
## Creación manual del contenedor WordPress

Posteriormente se creó el contenedor WordPress y se lo vinculó con la base de datos creada anteriormente.

Comando utilizado:

```bash
docker run -d --name wordpress --link wordpress-db:mysql --mount type=bind,source="${PWD}\wordpress",target=/var/www/html -e WORDPRESS_DB_USER=manager -e WORDPRESS_DB_PASSWORD=secret -p 8081:80 wordpress:4.9.8
```

## Captura 3 - Creación del contenedor WordPress

![Creación del contenedor WordPress](Capturas-ejem02/container-wordpress.jpg)

---
## Verificación del despliegue

Se verificó que ambos contenedores estuvieran ejecutándose correctamente.

Comando utilizado:

```bash
docker ps
```

## Captura 4 - Contenedores en ejecución

![Contenedores en ejecución](Capturas-ejem02/docker-ps.jpg)

---
## Resultado final

Finalmente se accedió desde el navegador al servicio WordPress desplegado mediante Docker.

URL utilizada:

http://localhost:8081

## Captura 5 - WordPress funcionando

![WordPress funcionando](Capturas-ejem02/localhost.jpg)
![WordPress funcionando](Capturas-ejem02/localhost-2.jpg)

---
## Conclusión

Se interpretó el funcionamiento del script run.sh, se ejecutaron manualmente todos sus comandos desde la terminal de Visual Studio Code y se verificó el correcto despliegue de los contenedores MariaDB y WordPress utilizando Docker.


