SYSTEMD JAVA 
ACCEDEMOS A SISTEM 

    cd /etc/systemd/system 

CREAMOS EL ARCHIVO DE SERVICIO 

    sudo touch generationg1.service 

EDITAMOS EL ARCHIVO DE SERVICIO 

    sudo nano generationg1.service 

PEGAMOS EN EL ARCHIVO 

[Unit] 
Description=Application using Spring Boot 
After=syslog.target 
[Service] 
User=ubuntu 
ExecStart=/usr/bin/java -jar /var/springApp/generationg1.war 
SuccessExitStatus=143 
[Install] 
WantedBy=multi-user.target 
 
REINICIAMOS EL DAEMON 
sudo systemctl daemon-reload 
ACTIVAMOS EL SERVICIO 
sudo systemctl enable generationg1.service 
ACTIVAMOS EL SERVICIO Y VEMOS EL ESTADO 
sudo systemctl start generationg1    
systemctl status generationg1 

 OTROS COMANDOS 
sudo systemctl stop generationg1 
 
sudo systemctl restart generationg1 
 
