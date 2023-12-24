# Creando una instancia EC2 en AWS

- Creando un par de llaves para SSH
    - Desde cualquier terminal con ssh-keygen disponible, generar un nuevo par de llaves para SSH.
    - Utilizando ```ssh-keygen``` crear un par de llaves con las siguientes características:
        - Algoritmo: RSA
        - Bytes: 4096
        - Comentario: keys_lab01
    - Las llaves deberán crearse en la carpeta por defecto y con el nombre por defecto (id_rsa).
    - No se definirá un passphrase, es decir, este campo debe quedar vacío.
    - Tomar nota de la ubicación de los archivos correspondientes a las llaves.
- Creando una instancia de EC2 en AWS
    - Loguearse con la cuenta root a AWS.
    - Crear un usuario nuevo y asignarle 'AdministratorAccess' policy directamente.
    - Loguearse con el usuario nuevo
    - Importar la llave pública generada anteriormente, con las siguientes características:
        - Nombre: keys_lab01
    - Crear una instancia de EC2 con las siguientes características:
        - Nombre: ubuntu_aws
        - Instance type: t2.micro
        - AMI: Ubuntu 22.04 (free tier)
        - Key par name: keys_lab01
        - Añadir grupo de seguridad que permita tráfico SSH desde 0.0.0.0/0
    - Cuando la instancia termine de crearse, identificar la IP pública para conectarse mediante SSH.
    - Investigar cuál es el usuario por default para el AMI utilizada.
    - Conectarse mediante SSH la instancia creada.

