# Instalando Python

## Creando y conectándose a un servidor con Linux
- Crear un servidor con Linux Ubuntu 22.04 `dev-server`
- Crear un par de llaves de SSH. Añadir la llave pública a `dev-server`
- Conectarse a `dev-server` mediante SSH utilizando las llaves de SSH previamente creadas.
- Modificar el archivo `/etc/ssh/sshd_config` de forma que:
    - El servicio SSHD solamente responda en el puerto 2222.
    - La autenticación de SSH mediante contraseña quede deshabilitada. Es decir, SSH solamente debe funcionar con llaves.
    - Nota: SSH funciona por defecto con el puerto 22. Cuando se corre el comando `ssh user@host` es lo mismo que correr `ssh -p 22 user@host`, l cual significa que si el servidor de SSH tiene otro puerto configurado, hay que especificarlo en el comando.
- Verificar que las configuraciones mencionadas funcionan conectándose mediante SSH utilizando llaves.

## Instalando Python
- Instalar [pyenv](https://github.com/pyenv/pyenv-installer).
    - Una vez instalado, seguir las instrucciones para configurarlo correctamente:
```
WARNING: seems you still have not added 'pyenv' to the load path.

# Load pyenv automatically by appending
# the following to
# ~/.bash_profile if it exists, otherwise ~/.profile (for login shells)
# and ~/.bashrc (for interactive shells) :

export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"

# Restart your shell for the changes to take effect.

# Load pyenv-virtualenv automatically by adding
# the following to ~/.bashrc:

eval "$(pyenv virtualenv-init -)"
```
- Desconectarse del servidor e ingresar nuevamente, verificar que `pyenv` funciona.

## Instalando Python con pyenv
- Identificar la versión estable de Python más reciente: https://www.python.org/downloads/source/
- Buscar la versión más reciente de Python utilizando los comandos de pyenv:
    - `pyenv install --list | grep 3.12.*`
- Instalar la versión más reciente:
    - `pyenv install 3.12.*`
- Resolver los problemas:
    - Pyenv descarga el código fuente de la versión seleccionada, lo compila y lo instala. Esta es una forma de instalar Python, pero a diferencia de otros métodos, puede requerir ciertas librerías adicionales para compilar Python. Otros métodos descargan e instalan una versión de Python que ya fue previamente compilada.
    - Identificar el error específico que ocasiona que Python no compile y buscar en internet con ese código de error, hasta que finalmente Python compile y se instale.
- Establecer la versión de Python instalada como la versión global de Linux:
    - `pyenv global 3.12.*`

