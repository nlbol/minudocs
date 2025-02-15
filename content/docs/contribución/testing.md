---
title: Testing
type: docs
prev: docs/contribución/
next: 
weight: 1
---

Si desea contribuir con testing, es recomendable que tome importancia a la información que se 
tiene registrado, esta información tiene las funciones esenciales de este proyecto y al mismo 
tiempo de MiniOS.

### Archivo de configuración
En MiniOS y Minunux, existe un archivo llamado `minios.conf` en el directorio `/etc/minios/`

Es necesario cambiar sus valores de dichos parametros para verificar que estos funcionen correctamente


```bash {filename="bash"}
USER_NAME="estudiante"
USER_PASSWORD="nucleolinux"
ROOT_PASSWORD="toor"
HOST_NAME="minios"
DEFAULT_TARGET="graphical"
ENABLE_SERVICES="docker"
DISABLE_SERVICES=""
SSH_KEY="authorized_keys"
CLOUD="false"
SCRIPTS="true"
HIDE_CREDENTIALS="true"
AUTOLOGIN="false"
SYSTEM_TYPE="puzzle"
EXPORT_LOGS="false"
CORE_BUNDLE_PREFIX="00-core"
BEXT="sb"
```


Hay algunos parámetros que solo se pueden cambiar antes del primer arranque, los siguientes parámetros pueden cambiar sin presentar fallas:

```bash {filename="bash"}
USER_PASSWORD
ROOT_PASSWORD
ENABLE_SERVICES
DISABLE_SERVICES
SSH_KEY
HIDE_CREDENTIALS
AUTOLOGIN
```


### Parámetros de arranque

Sea modo LEGACY o UEFI

Incompleto
