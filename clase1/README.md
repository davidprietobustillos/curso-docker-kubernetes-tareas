# Nombre Aplicacion
MYSQL

# Comandos ejecutados
docker run --name mi-mysql -e MYSQL_ROOT_PASSWORD=my-password -p 3333:3306 -d mysql:latest  

## Verificar que se creo el contenedor
docker ps
![mostrar que el existe el contenedor](docker_ps.png)

## Consulta los logs del container
docker logs mi-mysql   

# Accede al servicio (navegador para httpd, logs para redis/mysql) 
docker logs some-mysql
![mostrar el log de mysql](docker_logs_mi_mysql.png)

# Limpieza
![mostrar que se borro el contenedor y la imagen](docker_remove_image_and_container.png)
