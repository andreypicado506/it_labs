# Creando servidores y conectándose a ellos

## Crear una máquina virtual en Hyper-V
- Crear un servidor Linux en Hyper-V con las siguientes características:
    - Name: `servidor_a`
    - Generation: Generation 1 
    - Startup memory: 2048  
    - Connection: `...Virtual Switch`
    - Connect Virtual Hard Disk:
        - `Create a virtual hard disk`
        - Name: `ubuntu01ssd.vhdx`
        - Location: default
        - Size: 20GB
    - Installation Options: 
        - `Install an operating system from a bootable CD/DVD-ROM`
        - `C:\Users\Administrator\Downloads\ubuntu-22.04 1-live-server-amd64.iso`

## Instalando Ubuntu Server 22.04
### Servidor A
- Conectarse a la máquina virtual creada a través de la interfaz de `Hyper-V Manager`.
- Presionar `Start`.
- Pasos para la instalación:
    - 1. Desde el menú de booteo, seleccionar `* Try or install Ubuntu server`
    - 2. Seleccionar el lenguaje.
    - 3. Si hay un nuevo instalador disponible (`Installer update available`) seleccionar `Continue without updating`
    - 4. Keyboard configuration: `default`
    - 5. Choose type of install: `Ubuntu Server`
    - 6. Network connections: `eth0` debe operar con `DHCPv4` (notar que esta es la configuración por defecto). Verificar que `eth0` obtuvo una IP.
    - 7. Configure proxy: `default`.
    - 8. Configure Ubuntu archive mirror: `default`.
    - 9. Guided storage configuration: Seleccionar `Use an entire disk` y `Set up this disk as an LVM group`
    - 10. Profile setup:
        - Your name: `linux_lab`
        - Your servers name: `servidor_a`
        - Pick a user name: `linux_lab`
        - Choose a password: `*******`
    - 11. SSH setup:
        - Install OpenSSH server
    - 12. Featured Server Snaps: `default
- Esperar a que la instalación finalice.
- Una vez terminada la instalación, conectarse al servidor mediante SSH utilizando usuario y contraseña.

### Servidor B
- Desde el Hyper-V Manager hacer clic secundario sobre `servidor_a` y seleccionar `Export...` seleccionando como folder de destino `D:\Base_disks\ubuntu_export`.
- Desde el Hyper-V Manager hacer clic en la opción `Import Virtual Machine` y seleccionar el folder en donde previamente se exportó `servidor_a`. Finalmente, seleccionar `Copy the virtual machine...`.
- Verificar que el servidor se encuentra operativo y conectarse mediante SSH. Una vez hecho esto, cambiar el hostname por `servidor_b`.

## Creando una llave de SSH para conectar `servidor_a` y `servidor_b`
- Desde `servidor_a` utilizar `ssh-keygen` y crear un par de llaves con las siguientes características:
    - Algoritmo: RSA
    - Bytes: 4096
    - Comentario: keys_lab01
- Las llaves deberán crearse en la carpeta por defecto y con el nombre por defecto (id_rsa).
- No se definirá un passphrase, es decir, este campo debe quedar vacío.
- Tomar nota de la ubicación de los archivos correspondientes a las llaves.

- Desde `servidor_b` agregar el contenido de la llave pública previamente creada al archivo correspondiente (`authorized_keys`).
- Desde `servidor_a` conectarse a `servidor_b` utilizando la llave previamente creada (id_rsa).

## Ejercicios:
- Creando una llave nueva o utilizando la ya creada, conectarse mediante SSH desde `servidor_b` a `servidor_a`
- Genere una llave nueva y copiela al servidor remoto utilizando `ssh-id-copy`
- Cambie los permisos de una llave privada a `777` e intente conectarse nuevamente.
