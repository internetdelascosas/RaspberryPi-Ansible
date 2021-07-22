# RaspberryPi-Ansible
Colección de scripts Ansible que permiten la instalación de una Raspberry Pi - IoT Server desde cero.

Los scripts estan actualizados para la versión Raspbian GNU/Linux 10 (buster).

## Instalación
Para instalar los pasos son:

1. Realizar un update (siempre es recomendable)

```bash
$ sudo apt-get update
```

2. Instalar Ansible

```bash
sudo apt-get install ansible
```

3. Instalar git

```bash
$ sudo apt-get install -y git
```

4. Clonar el repositorio

```bash
$ git clone https://github.com/internetdelascosas/RaspberryPi-Ansible.git
```
## Ejecutar

Para ejecutar el playbook raspberrypi.yml que instala nginx, php, php7.3-fpm y MariaDB hay que entrar en la carpeta donde quedó el repositorio clonado y luego ejecutar el comando ansible-playbook con sudo tal como se muestra en las siguientes líneas.

```bash
$ cd RaspberryPi-Ansible

$ sudo ansible-playbook raspberrypi.yml -i inventario.yml
```

## Configuración

Al ejecutarse exitosamente Ansible, se instalará el servidor web nginx y la base de datos MariaDB.

Por defecto el usuario root de MariaDB tiene la contraseña vacía y solo se conecta usando sockets de linux. Debes cambiarla ejecutando los siguientes comandos

```bash
$ sudo mysql -u root -e 'UPDATE mysql.user SET password=PASSWORD("mypassword") where user = "root";'
$ sudo mysql -u root -e 'UPDATE mysql.user SET plugin="mysql_native_password"; flush privileges;'
```

Obviamente deben cambiar la password "mypassword" por su propia contraseña siguiendo la política de contraseñas fuertes.

Puedes acceder a la carpeta raíz del sitio web apuntando con tu navegador a la dirección de tu Raspberry Pi en la red interna, por ejemplo http://192.168.1.10

El software para administración de bases de datos phpmyadmin queda instalado en http://direccion_ip/db, recuerda que debes cambiar la direccion_ip por la que tu Raspberry Pi tiene asignada en el router.

## Consultas y Colaboración

Escribir a contacto@iot.cl
