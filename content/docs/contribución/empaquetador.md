---
title: Empaquetador
type: docs
weight: 3
prev:
next:
---

La siguiente guía es para explicar como empaquetar un programa de manera simple.
> Nota.- esta guía no tiene incluido la descripción y/o explicación de la construcción o compilación de un programa.

### Directorio de trabajo, ejemplo: 

```bash {filename="ejemplo"}
nombre_version_arch
```

Ejemplo el paquete Hola Mundo que cuenta con estas características:
- `nombre: hola-mundo`
- `versión: 1.0.2`
- `arquitectura: amd64`

el directorio que debe de crearse es el siguiente:  

```bash {filename="comando"}
mkdir hola-mundo_1.0.2_amd64
```


### DEBIAN

Se debe crear un subdirectorio llamado DEBIAN, este subdirectorio aloja ficheros importantes del paquete, para ser especifico el fichero `control`  
Contenido de ejemplo del fichero control:

```bash {filename="control"}
Package: hola-mundo
Version: 1.0.2
Section: devel
Priority: extra
Architecture: amd64
Replaces: hola-mundo
Installed-Size: 
Maintainer: User Name <username0@example.com>
Homepage: https://example.com/
Description: Breve descripción del paquete
```

### Agregar el tamaño 
En el fichero `control` existe una parametro llamado `Installed-Size:` , en este parametro se debe agregar el tamaño en `kilobytes (KB)`  

```bash {filename="comando"}
fernando@home:~$ du -ks hola-mundo_1.0.2_amd64/
1563 hola-mundo_1.0.2_amd64

```

Este valor `1563` se debe agregar al parámetro donde se especifica el tamaño del paquete.

## IMPORTANTE

Si el paquete que esta creando requiere dependencias, es necesario agregar este parámetro junto con las dependencias y en lo posible las versiones especificas

```bash {filename="texto"}
Depends: iptables, ufw, etc
```

## Resumen

El contenido de este directorio debe tener la siguiente estructura

```bash {filename="ejemplo"}
hola-mundo_1.0.2_amd64/          # directorio del paquete
├── bin                          # directorio /bin
│   └── holamundo                # binario, comando o script "holamundo"
└── DEBIAN                       
    └── control

    2 directories, 2 files
```

> el directorio DEBIAN y archivo control es muy importante para la creación de un paquete y que este tenga un control cuando se instala

## Creación de paquete DEB

Una vez se tenga listo todo el directorio de trabajo, solo se necesita crear el paquete desde el directorio de trabajo

```bash {filename="comando"}
fernando@home:~$ dpkg-deb -b hola-mundo_1.0.2_amd64/
...
hola-mundo_1.0.2_amd64.deb  <- paquete creado
```

Este comando podrá generar un paquete .deb listo para instalarse mendiante el comando dpkg o apt (recomendable)
