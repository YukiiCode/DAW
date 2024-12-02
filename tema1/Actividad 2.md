# Actividad 2

Creación de 3 ejercicios sobre scripts

#### 1. Crea un script que añada un puerto de escucha en el fichero de configuración de Apache. El puerto se recibirá como parámetro en la llamada y se comprobará que no esté ya presente en el fichero de configuración.

```bash
if["$#" -ne "1"]
then
	echo "falta num puerto"
else 
	echo "correcto"
	GREP "LISTEN$1" "/etc/apache2/parts.conf"
	if["$?" eq 0]
	then
		echo "Listen ya encontrado en ports.conf"
	else
		echo "Listen añadido"
		echo "Listen $1" >> "/etc/apache2/ports.conf"
	fi
fi
```

Este script verifica si se proporciona un número de puerto como argumento. Si no, muestra un mensaje indicando que falta el puerto. Si el puerto está presente, comprueba si ya existe una línea en el archivo ports.conf de Apache con ese puerto:

* Si la línea ya existe, muestra un mensaje indicando que el puerto ya está configurado.
* Si no existe, añade la línea con el puerto al final de ports.conf.



#### 2. Crea un script que añada un nombre de dominio y una ip al fichero hosts. Debemos comprobar que no existe dicho dominio en el fichero hosts

```bash
if [ "$#" -ne 2 ]; then
    echo "Uso: $0 <IP> <dominio>"
    exit 1
fi

IP="$1"
DOMINIO="$2"
HOSTS_FILE="/etc/hosts"

# Verifica si el dominio ya existe en el archivo /etc/hosts
if grep -q "\s$DOMINIO$" "$HOSTS_FILE"; then
    echo "El dominio '$DOMINIO' ya existe en $HOSTS_FILE"
else
    # Si no existe, añade la IP y el dominio al archivo hosts
    echo "$IP $DOMINIO" | sudo tee -a "$HOSTS_FILE" > /dev/null
    echo "Añadido: $IP $DOMINIO a $HOSTS_FILE"
fi
```



#### 3. Crea un script que nos permita crear una página web con un título, una cabecera y un mensaje

```bash
# Pide al usuario el título, la cabecera y el mensaje
read -p "Introduce el título de la página: " TITULO
read -p "Introduce el texto de la cabecera: " CABECERA
read -p "Introduce el mensaje del cuerpo: " MENSAJE

# Nombre del archivo HTML
ARCHIVO="pagina.html"

# Genera el contenido HTML y lo guarda en el archivo
cat <<EOF > "$ARCHIVO"
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>$TITULO</title>
</head>
<body>
    <h1>$CABECERA</h1>
    <p>$MENSAJE</p>
</body>
</html>
EOF

# Confirmación
echo "La página web '$ARCHIVO' se ha creado con éxito."
```
