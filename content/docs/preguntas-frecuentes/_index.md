---
title: Preguntas frecuentes
type: docs
#prev: docs/first-page
#next: docs/folder/leaf
sidebar:
  open: true
---


**1. ¿Cuales son las credenciales?**  
Las credenciales son:  
`estudiante:nucleolinux`  
`root:toor`

**2. ¿Es posible instalar como Dualboot?**  
Respuesta corta, NO

**3. Error: /minios/boot/vmlinuz has invalid signature.**  
Necesita desactivar la opción "Secure Boot" de la BIOS/EUFI SetUp, esto se debe a que el kernel no esta firmado

**4. ¿ Por que el kernel no esta firmado?**  
El kernel no esta firmado para tener la integración de AUFS y NTFS3
