# SSH

Ingresar a servidor

    chmod 400 file.pem
    ssh -i file.pem ubutnu@ip_public
    ssh -i file.pem -L 3333:localhost:3036 ubutnu@18.216.218.38

Actualizar

    sudo apt-get update
    sudo apt-get upgrade


Instalaciones:

>MYSQL

    sudo apt install mysql-server -y

    sudo mysql_secure_installation

> Bajarle permisos de password

    SHOW VARIABLES LIKE 'validate_password%';
    SET GLOBAL validate_password.policy=LOW;
    SET GLOBAL validate_password.length=6;

> Crear usuario
CREATE USER 'gguzman'@'localhost' IDENTIFIED BY 'admin1234';

GRANT ALL PRIVILEGES ON *.* TO 'gguzman'@'localhost' WITH GRANT OPTION;

CREATE USER 'gguzman'@'%' IDENTIFIED BY 'admin1234';
GRANT ALL PRIVILEGES ON *.* TO 'gguzman'@'%' WITH GRANT OPTION;

Cambiar clave usuario

    SET PASSWORD FOR 'gguzman'@'%' = 'Admin1234';

    FLUSH PRIVILEGES;

sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
cambiar bind addres por 0.0.0.0 para poder entrar remotamente


## DEPLOY SPRING BOOT

Subir archivos a instancia

scp -i generationg1.pem deployg1.war ubuntu@18.216.218.38:~/

    Crear carpeta 

sudo mkdir /var/springApp

    Mover el war a la carpeta creada

sudo mv ~/gato.war /var/springApp/APACHE

    Instalamos apache

sudo apt-get install apache2 -y

    Ahora necesitamos decirle a Apache que envíe la solicitudes proxy a nuestra aplicación.

    Set up proxy

sudo a2enmod proxy
sudo a2enmod proxy_ajp
sudo systemctl restart apache2

    Abra el archivo virtual conf.

cd /etc/apache2/sites-available/
 sudo nano 000-default.conf

    AGREGAR al final antes de </VirtualHost>

ProxyPass / ajp://localhost:9090/
ProxyPassReverse / ajp://localhost:9090/

    Reiniciamos apache

sudo systemctl restart apache2

    Instalamos java

sudo apt-get install default-jdk -y
sudo apt install openjdk-18-jdk

    Acceder a la carpeta

cd /var/springApp/

    Ejecutamos el war

java -jar deployg1.war

Reiniciar maquina

    sudo reboot