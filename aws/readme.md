# Instalación y Configuración de Apache en AWS

> [!Warning]
> He intentado utilizar aws pero he tenido problemas a la hora de usarlo para la actividad, para no dejar sin entregar nada, he documentado los pasos que hay que hacer para la actividad


## Paso 1: Conectarse a la Instancia de AWS

Conéctate a tu instancia EC2 usando SSH:

```sh
ssh -i "ruta/a/tu/clave.pem" ec2-user@tu-direccion-ip-o-dns
```

## Paso 2: Actualizar los Paquetes del Sistema

Actualiza los paquetes del sistema a la última versión:
```sh
sudo apt update && sudo apt upgrade -y
```

## Paso 3: Instalar Apache

Instala Apache en tu instancia:
```sh
sudo apt install apache2 -y
```

## Paso 4: Iniciar y habilitar Apache

Inicia y habilita Apache para que se ejecute al iniciar el sistema:
```sh
sudo systemctl start apache2
sudo systemctl enable apache2
```

## Paso 5: Instalar MySQL y el Módulo de Autenticación

Instala MySQL y el módulo de autenticación para Apache:
```sh
sudo apt install mysql-server -y
sudo apt install libapache2-mod-auth-mysql -y
```

## Paso 6: Configurar la Autenticación con MySQL

Edita el archivo de configuración de Apache para habilitar la autenticación con MySQL:
```sh
sudo nano /etc/apache2/apache2.conf
```

Con esta configuración: 
<Directory "/var/www/html">
    AuthName "Área Restringida"
    AuthType Basic
    AuthBasicProvider mysql
    AuthMYSQLEnable On
    AuthMySQLHost localhost
    AuthMySQLUser tu_usuario_mysql
    AuthMySQLPassword tu_contraseña_mysql
    AuthMySQLDB tu_base_de_datos
    AuthMySQLUserTable tu_tabla_de_usuarios
    AuthMySQLNameField nombre_de_usuario
    AuthMySQLPasswordField contraseña
    Require valid-user
</Directory>

Nota: Reemplaza los valores como tu_usuario_mysql, tu_contraseña_mysql, tu_base_de_datos, etc., con los valores correspondientes a tu configuración.

Guarda y cierra el archivo.

## Paso 7: Crear un Certificado Autofirmado y Activar SSL

Instala OpenSSL y crea un certificado autofirmado:
```sh
sudo apt install openssl -y
```

Genera el certificado autofirmado:
```sh
sudo mkdir -p /etc/ssl/private

sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
-keyout /etc/ssl/private/apache-selfsigned.key \
-out /etc/ssl/certs/apache-selfsigned.crt
```

## Paso 8: Configurar Apache para Usar SSL

Edita el archivo de configuración SSL de Apache:
```sh
sudo nano /etc/apache2/sites-available/default-ssl.conf
```

Busca y actualiza las líneas para que apunten a tu certificado y clave:
SSLCertificateFile /etc/ssl/certs/apache-selfsigned.crt
SSLCertificateKeyFile /etc/ssl/private/apache-selfsigned.key

Guarda y cierra el archivo.

## Paso 9: Habilitar el Módulo SSL y el Sitio SSL

Habilita el módulo SSL y el sitio SSL en Apache:
```sh
sudo a2enmod ssl
sudo a2ensite default-ssl
```
## Paso 10: Reiniciar Apache

Reinicia Apache para aplicar los cambios:
```sh
sudo systemctl restart apache2
```

## Paso 11: Verificar la Configuración

Abre tu navegador web y navega a https://tu-direccion-ip-o-dns. Deberías ver la página de inicio de Apache y se te solicitarán credenciales debido a la autenticación.

Nota: Es posible que veas una advertencia en el navegador sobre el certificado autofirmado. Puedes continuar de forma segura, ya que sabes que es tu propio certificado.
