---
title: Balena Etcher
type: docs
prev: 
next: booteable
weight: 5
---


* Soporte de instalación  
    * Legacy BIOS
    * EFI


Balena Etcher permite crear un pendrive booteable, Minunux hereda las caracteristicas de MiniOS, esto significa que es posible instalar Minunux utilizando simplemente BalenaEtcher.  

<img src="https://raw.githubusercontent.com/nlbol/recursos/refs/heads/main/wiki/img/balena-etcher/balena-etcher-01.png" width="539" height="300" alt="Image description">  


## Decarga

Descargar Balena Etcher en formato AppImage  

```bash {filename="GitHub"}
https://github.com/balena-io/etcher/releases

```

> Descargar el archivo con extensión .AppImage

## Ejecutar

Asegurate de que el archivo AppImage tenga permisos de ejecución, hay 2 maneras de asignar permisos: utilizando la terminal o utilizando el explorador de archivos.

<img src="https://raw.githubusercontent.com/nlbol/recursos/refs/heads/main/wiki/img/balena-etcher/balena-etcher-02.png" width="539" height="300" alt="Image description">  

Este seria un ejemplo practico usando la terminal.  

```bash {filename=bash}
chmod +x balena-etcher-*.AppImage
```

## Instalación

Los pasos para instalar Minunux en un pendrive usando Balena Etcher son 3 pasos simples:

### Paso 1: Seleccionar la Imagen ISO


<img src="https://raw.githubusercontent.com/nlbol/recursos/refs/heads/main/wiki/img/balena-etcher/balena-etcher-03.png" width="539" height="300" alt="Image description">  

> usar la opción: Flash from file  


### Paso 2: Seleccionar el dipositivo

<img src="https://raw.githubusercontent.com/nlbol/recursos/refs/heads/main/wiki/img/balena-etcher/balena-etcher-04.png" width="539" height="300" alt="Image description">  


Seleccione el dispositivo disponible de la lista que se muestra, identifique el pendrive deseado.

<img src="https://raw.githubusercontent.com/nlbol/recursos/refs/heads/main/wiki/img/balena-etcher/balena-etcher-05.png" width="539" height="300" alt="Image description">  

> En la imagen se muestra un ejemplo de un pendrive "SanDisk Cruzer_Blade" de 16GB (15.4 GB).


### Seleccionar la opción "FLASH"

Esta opción va permitir flashear la imagen ISO en el pendrive, Minunux auotmaticamente hara su instalación correspondiente en el primer arranque.

<img src="https://raw.githubusercontent.com/nlbol/recursos/refs/heads/main/wiki/img/balena-etcher/balena-etcher-06.png" width="539" height="300" alt="Image description">  

En este momento, la imagen esta siendo cargada en el dispositivo, por favor no interrumpa este proceso

<img src="https://raw.githubusercontent.com/nlbol/recursos/refs/heads/main/wiki/img/balena-etcher/balena-etcher-07.png" width="539" height="300" alt="Image description">  

Si esta siguiendo esta guía al pie de la letra, es muy seguro que la finalizar, tendra una ventana identica a esta donde muestra que el proceso de "FLASH" termino exitosamente.

<img src="https://raw.githubusercontent.com/nlbol/recursos/refs/heads/main/wiki/img/balena-etcher/balena-etcher-08.png" width="539" height="300" alt="Image description">  

Ahora podra ejcutar MiniOS desde el pendrive con persistencia.