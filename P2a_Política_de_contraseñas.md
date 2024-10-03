# Política de contraseñas

## Contexto
Por defecto, la mayoría de sistemas operativos, vienene con una política de contraseña muy laxa, una contraseña segura presenta una barrera más al atacante, que en su intento de acceder al sistema, indudablemete dejará más rastro y en algunos casos a provocar el abandondo de ataque.

## Objetivos
* Entender el sistema de contraseñas del sistema operativo linux
  * El sistema de contraseñas de linux consta de dos apartados:
    * Lista de usuarios: /etc/passwd --> se guardan guardan todos los nombres de usuario, las contraseñas, los UID/GID, y los GECOS(nombre completo del usuario).
    * Contraseñas ocultas y cifradas: /etc/shadow --> se guardan los usuarios y sus contraseñas cifradas.
    * Listas de grupo: /etc/group --> se guardan los nombres de grupo y sus contraseñas.

* Entender el PAM (Plugable authentication Module)
  * El PAM
    * El Pluggable Authentication Modules (PAM) es una infraestructura de inicio de sesión UNIX integrada. Los componentes de entrada del sistema utilizan PAM, como el gestor de visualización de dtlogin del entorno de escritorio común, para autenticar a los usuarios que inician sesión en un sistema UNIX.
* Instalar y configurar la libreria _pwquality_
### Instalación
```bash
sudo apt install libpwquality-tools libpam-pwquality
```
### Configuración
```bash
nano /etc/security/pwquality.conf
```
* Editamos el archivo:

```bash
minlen = 6
dcredit = -1
ucredit = -1
lcredit = -1
ocredit = -1
```
* Revisamos las líneas para comprobar si esta bien configurado:

```bash
sudo nano /etc/pam.d/common-password
```
* Miramos si tenemos el comando:

```bash
password requisite pam_pwquality.so retry=3
```

* Comprobar y verificar que se ha llevado la práctica de forma correcta

```bash
sudo passwd alumnom
```

