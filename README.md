# Actividad Docker - DAD

## Alumna: Tiziana Yazmin Ochoa

## Materia: Diseño y Arquitectura de Despliegues

## Fecha: 05/05/2026

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

![Construcción de la imagen](build.jpg)

---

## Verificación de la imagen creada

Se verificó que la imagen estuviera disponible localmente.

Comando utilizado:

```bash
docker images
```

### Captura 2 - Imagen creada

![Imagen creada](docker-images.jpg)

---

## Ejecución del contenedor

Se ejecutó el contenedor asociado a la imagen creada.

Comando utilizado:

```bash
docker ps
```

### Captura 3 - Contenedor en ejecución

![Contenedor en ejecución](docker-ps.jpg)

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

![Edición de indez](index-html.jpg)

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

![Version de Vim](vim-version.jpg)
![Version de Vim](vim-version-2.jpg)

## Resultado Final

Se verificó el correcto funcionamiento accediendo desde el navegador al servicio publicado por Docker.

URL utilizada:

```text
http://localhost:8080
```

### Captura 7 - Página funcionando

![Página funcionando](localhost.jpg)

---

## Conexión desde Visual Studio Code

Se instaló la extensión Remote Explorer para conectarse al contenedor Docker desde Visual Studio Code.

### Captura 8 - VS Code conectado al contenedor

![Conteiner en VS code](vscode-conteiner.jpg)

---

# Ejemplo 02

*Esta sección será completada posteriormente.*
