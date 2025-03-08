# Actividad 3

## Descargar la imagen de ubuntu, hello-world, nginx

- Para descargar las imagenes lo haremos con el mismo comando
```bash
docker pull "imagen"
```
![image](https://github.com/user-attachments/assets/fb2278c5-a479-4e80-9224-47791168b769)
![image](https://github.com/user-attachments/assets/bb8ae7d3-8286-4bc6-9d79-93d2a790adb6)
![image](https://github.com/user-attachments/assets/df1a655d-ba1c-4fc1-9c50-989a2d460a11)

- Listado de todas las imagenes
![image](https://github.com/user-attachments/assets/30d68ef7-77ee-47a5-aea6-5aff962bde3e)

- Ejecuta un contenedor hello-world y dale nombre “myhello1” , “myhello2” y “myhello3” 

```bash
docker run --name myhello1 hello-world
docker run --name myhello2 hello-world
docker run --name myhello3 hello-world
```
![image](https://github.com/user-attachments/assets/c344a049-c3b6-4685-bfe0-8b8e01935348)
![image](https://github.com/user-attachments/assets/027c5ac4-86ed-4105-99c2-fea4f9712296)
![image](https://github.com/user-attachments/assets/010dc985-fb97-4991-96ab-3b27570e1d4d)

- Para ver los contendores usamos el siguiente comando
```bash
docker ps -a
```
![image](https://github.com/user-attachments/assets/00ec7e93-09ee-4063-8787-aa67a574e2cd)

- Para el contenedor "myhello1", "myhello2”

![image](https://github.com/user-attachments/assets/4808aca0-1b9e-4055-bb4a-13c39fd7595f)

- Borramos "myhello1"
```bash
docker rm myhello1
```

- Contenedores actuales
![image](https://github.com/user-attachments/assets/9c75e45a-3b0b-4c08-b51b-b28824dd52b9)


- Borra todos los contenedores

![image](https://github.com/user-attachments/assets/7490e83f-dfb7-4f9d-a0ed-668b4bfc250e)
