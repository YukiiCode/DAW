# Actividad 2 Docker

> **Nota:** 
> Como la instalación no habia que documentarla he omitido el paso, pero he instalo docker en ubuntu siguiendo los pasos de la pagina oficial de docker
> https://docs.docker.com/get-started/

## Primera parte

### 1. Ejecuta la imagen "hello-world"

```bash
docker run hello-world
```

![image](https://github.com/user-attachments/assets/1cb6b07c-3cef-4b7e-b6f4-ebebf8fb94c3)

Esto descargará una imagen de prueba y mostrará un mensaje de éxito

### 2 .Muestra las imágenes Docker instaladas

```bash
docker images
```
![image](https://github.com/user-attachments/assets/1bb9c80e-a784-47ba-89b5-d3aa7d178b56)

Este comando muestra las imagenes que tenemos en nuestro sistema 

### 3. Muestra los contenedores Docker

```bash
docker ps
```
![image](https://github.com/user-attachments/assets/6d8c12f4-0a8f-493f-9a49-779285c2b949)

Este comando muestra los contenedores que tenemos en docker, en este caso no tengo ninguno creado

## Segunda Parte

### Edita el fichero Dockerfile

- Usamos el comando nano para acceder al dockerfile
```bash
nano dockerfile
```

- Escribir el contenido del Dockerfile
```dockerfile
# Usar una imagen base (en este caso, Python 3.9)
FROM python:3.9

# Mantener al autor (opcional)
LABEL maintainer="tu_nombre <tu_email@example.com>"

# Crear un directorio de trabajo dentro del contenedor
WORKDIR /app

# Copiar archivos locales al contenedor
COPY . /app

# Instalar dependencias (si tienes un archivo requirements.txt)
RUN pip install --no-cache-dir -r requirements.txt

# Comando por defecto al iniciar el contenedor
CMD ["python", "app.py"]
```

> Nota: Como es un contendor de python voy a crear un archivo para ejecutar para revisar si todo está correcto

- Contenido app.py (creado con nano)
```python
print("¡Hola desde Docker!")
```

- Prueba de que he realizado los pasos anteriores
![image](https://github.com/user-attachments/assets/a8a05b57-ab2c-48bd-8208-86a5a204aa5a)


### Construye el contenedor

```bash
docker build -t mi-aplicacion:latest
```

Explicación:

- t mi-aplicacion:latest : Asigna un nombre (mi-aplicacion) y una etiqueta (latest) a la imagen.
- . : Indica que el Dockerfile está en el directorio actual.

### Ejecútalo
### Create una cuenta en hub.docker.com
### Publícalo

