---
title: Metapaquetes
type: docs
weight: 4
next: preguntas-frecuentes
---

## ¿Que es un metapaquete?
Un metapaquete es un paquete que no contiene archivos ejecutables o configuraciones, sino que simplemente depende de otros paquetes. Esto permite instalar un conjunto de paquetes de manera sencilla con un solo comando.

En esta guía se va a describir 2 metodos para crear metapaquetes:  

- [Creación del metapaquete con equivs-control](#creación-del-metapaquete-con-equivs-control)
- [Creación del metapaquete manualmente sin equivs](#creación-de-un-metapaquete-manualmente-sin-equivs)

## Creación del metapaquete con equivs-control

### como instalar equivs

Para esta guía es necesario tener una distribución Debian o derivados, aunque se recomienda utilizar Minunux para utilizar los repositorios que tenga incluido.

```bash {filename="comando"}
sudo apt update && sudo apt install equivs -y
```


## Creación del metapaquete con equivs-control

### Paso 1: Crear el archivo de control

Ejecuta el siguiente comando para generar un archivo base de configuración:

```bash {filename=bash}
equivs-control mi-metapaquete
```

> Este comando generará un archivo llamado mi-metapaquete, esto es un template que necesita ser editado.  

El archivo tiene un formato similar a este:

```bash {filename="mi-metapaquete"}
### Commented entries have reasonable defaults.
### Uncomment to edit them.
# Source: <source package name; defaults to package name>
Section: misc
Priority: optional
# Homepage: <enter URL here; no default>
Standards-Version: 3.9.2

Package: <package name; defaults to equivs-dummy>
# Version: <enter version here; defaults to 1.0>
# Maintainer: Your Name <yourname@example.com>
# Pre-Depends: <comma-separated list of packages>
# Depends: <comma-separated list of packages>
# Recommends: <comma-separated list of packages>
# Suggests: <comma-separated list of packages>
# Provides: <comma-separated list of packages>
# Replaces: <comma-separated list of packages>
# Architecture: all
# Multi-Arch: <one of: foreign|same|allowed>
# Copyright: <copyright file; defaults to GPL2>
# Changelog: <changelog file; defaults to a generic changelog>
# Readme: <README.Debian file; defaults to a generic one>
# Extra-Files: <comma-separated list of additional files for the doc directory>
# Links: <pair of space-separated paths; First is path symlink points at, second is filename of link>
# Files: <pair of space-separated paths; First is file to include, second is destination>
#  <more pairs, if there's more than one file to include. Notice the starting space>
Description: <short description; defaults to some wise words>
 long description and info
 .
 second paragraph
```

### Paso 2: Editar el archivo de control
Edita el archivo con un editor de texto como nano:

```bash {filename="comando"}
nano mi-metapaquete
```

El archivo tiene un formato similar a este:


```bash {filename="mi-metapaquete"}
Section: misc  
Priority: optional  
Standards-Version: 4.5.1  
Package: mi-metapaquete  
Version: 1.0  
Maintainer: Tu Nombre <tuemail@example.com>  
Architecture: all  
Depends: vim, curl, git  
Description: Este es un metapaquete de ejemplo  
 Este metapaquete instala Vim, Curl y Git.
```

#### Explicación de los campos

- `Package:` Nombre del metapaquete.
- `Version:` Versión del metapaquete.
- `Maintainer:` Persona responsable del paquete.
- `Architecture:` Debe ser all ya que no contiene binarios.
- `Depends:` Lista de paquetes que se instalarán con el metapaquete.
- `Description:` Breve descripción del metapaquete.
- `Section:` Misc se usa cuando no encaja claramente en una categoria especifica.

> Al final de la guía, se va agregar información adicional sobre metapaquetes.


### Paso 3: Construcción del metapaquete

Ejecuta el siguiente comando para construir el metapaquete:  

```comando {filename="bash"}
equivs-build mi-metapaquete

```

Este comando generará un archivo `.deb`, por ejemplo:  

```bash {filename="comando"}
mi-metapaquete_1.0_all.deb
```

### Paso 4: Instalación del metapaquete  

Para instalar el metapaquete y sus dependencias, usa:

```bash {filename="comando"}
sudo apt install ./mi-metapaquete_1.0_all.deb
```

> Es posible usar `dpkg -i`  para la instalación, pero es mas recomendable usar `apt`  

## Creación de un metapaquete manualmente (sin equivs)

Si deseas crear un metapaquete sin `equivs`, puedes hacerlo manualmente de la siguiente manera:  

### Paso 1: Crear la estructura del paquete 

```bash {filename="comando"}
mkdir -p mi-metapaquete_version_arch/DEBIAN
```

### Paso 2: Crear el archivo de control con algun editor de texto (nano)

```bash {filename="comando"}
nano mi-metapaquete_version_arch/DEBIAN/control
```

Contenido del archivo:  

```bash {filename="mi-metapaquete"}
Package: mi-metapaquete  
Version: 1.0  
Section: misc  
Priority: optional  
Architecture: all  
Maintainer: Tu Nombre <tuemail@example.com>  
Depends: vim, curl, git  
Description: Metapaquete de ejemplo  
 Este metapaquete instala Vim, Curl y Git.
```

### Paso 3: Construcción del paquete

```bash filename="comando"
dpkg-deb --build mi-metapaquete_version_arch/
```

Esto generará `mi-metapaquete_version_arch.deb.`

### Paso 4: Instalación del metapaquete

```bash {filename="comando"}
sudo apt install ./mi-metapaquete_version_arch.deb -y
```


## Información adicional

Debian define una variedad de secciones para los paquetes deb, esta es una lista de secciones mas comunes a usar:  


- `admin:` Utilidades de administración del sistema.
- `devel:` Herramientas y bibliotecas de desarrollo.
- `doc:` Documentación y manuales.
- `editors:` Editores de texto y programas relacionados.
- `games:` Juegos y entretenimiento.
- `graphics:` Software relacionado con gráficos y diseño.
- `net:` Aplicaciones y utilidades de red.
- `utils:` Utilidades diversas.

> Vea más secciones en: [https://packages.debian.org/stable/](https://packages.debian.org/stable/)