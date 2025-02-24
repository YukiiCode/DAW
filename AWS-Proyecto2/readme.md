# Práctica AWS Segundo Trimestre

## Instalación de Wordpress en instancia Ubuntu EC2 con soporte de base de datos RDS y EFS

### Pasos a seguir

1. Entramos en el curso asignado de AWS y entramos en la consola para crear las instancias necesarias
2. Primero creamos la vpc

Configuracion empleada:  
![image](https://github.com/user-attachments/assets/40dbb658-5035-41d4-9b7a-a47eadfe8623)

Vista previa de las redes: ![image](https://github.com/user-attachments/assets/f2dfedd8-625c-4220-90c7-bfa4fa49cfe5)

A continuación pulsamos en Crear VPC y se crearan automaticamente los elementos configurados:
![image](https://github.com/user-attachments/assets/c06af47c-bddf-45f9-a0c0-eb99e9845076)

3. Creamos el Grupo de Seguridad
El grupo de seguridad será llamado seguridadwordpress
Con esta configuración:

![image](https://github.com/user-attachments/assets/a681f553-ffa0-48ed-ba02-d268a384d373)

Y nos conectamos a la instancia via ssh 

![image](https://github.com/user-attachments/assets/108577d8-fd75-4f5f-b61c-f1ff4cf047c3)

4. Apache y PHP

Usamos este comando para instalar apache en la instancia
```bash
sudo apt update
sudo apt install apache2
sudo systemctl start apache2 (Para arrancar el servidor.)
sudo systemctl enable apache2 (para que apache inicie cada vez que arranca la instancia.)
```

4.1 Comprobamos que nos mueste la ventana de bienvenida de apache al entrar en la ip pública

![image](https://github.com/user-attachments/assets/efed92b0-9c2d-4ea1-a517-9061ec612182)

 - Comprobamos que el paquete amazon-linux está instalado en el servidor
```bash
sudo apt -y update && sudo apt upgrade
```

 - Instalamos php como un módulo de Apache:
```bash
sudo apt install php7.4 libapache2-mod-php7.4 php7.4-cli
```

 - También necesitamos instalar mysql como módulo de apache:
```bash
sudo apt install php7.4-mysql
```

 - Y reiniciamos apache:
```bash
sudo systemctl restart apache2
```

5. Creación de la base de datos

![image](https://github.com/user-attachments/assets/8ac49e09-b56f-459d-9547-bc58fe3e031e)

 - Elegimos la capa gratuita
![image](https://github.com/user-attachments/assets/fc8c2194-a4d0-4f4c-8506-2cc7465da4f1)


Configuración adicional: 

![image](https://github.com/user-attachments/assets/25366377-b02d-468f-8686-659ccf5bc82f)

![image](https://github.com/user-attachments/assets/3f3a328e-66a8-4a68-8f88-6a0f7e5443b5)

![image](https://github.com/user-attachments/assets/467cc07a-8025-4fa9-a907-ce668fd00dbd)
