---
title: Clásico
type: docs
prev: docs/instalación
next:
weight: 1

---


* Soporte de instalación  
    * Legacy BIOS

En esta sección se va explicar sobre como realizar la instalación clásica (antigua), se va realizar los ejemplos en 2 sistemas operativos:

### GNU/Linux

Pasos para realizar la instalación de MiniOS Minunux

se recomienda verificar que los comandos usados en esta guía los tengan presentes en sus sistemas
Ejecutar los siguientes comandos:

**Identificar el dispositivo**

```bash {filename="bash"}
fernando@home:$ lsblk 
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931,5G  0 disk 
├─sda1   8:1    0     1G  0 part /boot/efi
├─sda2   8:2    0     1G  0 part /boot
├─sda3   8:3    0   702G  0 part /
└─sda5   8:5    0 227,5G  0 part 
sdb      8:16   0 111,8G  0 disk            <- dispositivo (pendrive) donde se desea instalar

```
> Advertencia: Tome en cuenta el nombre del dispositivo y que este no este montado  

**Preparando el dispositivo /dev/sdb**  

> los comandos se deben ejecutar como "root" o en su defecto "sudo"   
  

```bash  {filename="bash"}

dd if=/dev/zero of=/dev/sdb bs=4096 count=273  
echo -e "o\nn\np\n1\n\n\nw" | fdisk /dev/sdb   
mkfs.ext4 /dev/sdb1                            
mkdir -p /mnt/{iso,usb}                        
mount /dev/sdb1 /mnt/usb                       
mount minios*minunux*.iso /mnt/iso             
cp -r /mnt/iso/minios /mnt/usb                 
umount /mnt/iso                                
bash /mnt/usb/minios/boot/bootinst.sh          
umount /mnt/usb                                
rm -rf /mnt/{iso,usb}                          

```
reiniciar el equipo, iniciar desde el pendrive y Listo!
