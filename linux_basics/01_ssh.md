# Creando servidores y conectándose a ellos

## Crear una máquina virtual en Hyper-V
- Crear un servidor Linux en Hyper-V con las siguientes características:
    - Name: `ubuntu01`
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
- Conectarse a la máquina virtual creada a través de la interfaz de `Hyper-V Manager`.
- Presionar `Start`.
- Pasos para la instalación:
    - 1. Desde el menú de booteo, seleccionar `* Try or install Ubuntu server`
    - 2. Seleccionar el lenguaje.
    - 3. Si hay un nuevo instalador disponible (`Installer update available`) seleccionar `Continue without updating`
    - 4. Keyboard configuration: default
    - 5. Choose type of install: `Ubuntu Server`
    - 6. Network connections: `eth0` debe operar con `DHCPv4` (notar que esta es la configuración por defecto). Verificar que `eth0` obtuvo una IP.
    - 7. Configure proxy: default.
    - 8. Configure Ubuntu archive mirror: default.
    - 9. Guided storage configuration: Seleccionar `Use an entire disk` y `Set up this disk as an LVM group`
    - 10. Profile setup:
        - Your name: linux_lab
        - Your servers name: ubuntu_lab_01
        - Pick a user name: linux_lab
        - Choose a password: `*******`
    - 11. SSH setup:
        - Install OpenSSH server
    - 12. Featured Server Snaps: `default`

