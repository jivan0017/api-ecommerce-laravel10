# DOCKERIZANDO

- Se crea en la raíz misma que contiene el proyecto NEST, la carpeta /db, dentro de esta, el fichero: init.sql en cuyo contenido:

-- CREATE DATABASE IF NOT EXISTS codrrdb
SELECT 'CREATE DATABASE ventasdb'
WHERE NOT EXISTS (SELECT FROM pg_database WHERE datname = 'ventasdb')\gexec

- Ejecutar docker desktop

- Crear el fichero en la raíz misma del proyecto NEST, el fichero: docker-compose.yml

version: '3.1'

services:
  ventas_pg:
    image: postgres:15.1
    container_name: ventas_pg
    restart: always
    environment:
      POSTGRES_DB: ventasdb    
      POSTGRES_USER: ventasadmin
      POSTGRES_PASSWORD: secret1234
    volumes:
      - ./db/init.sql:/docker-entrypoint-initdb.d/init.sql
    ports:
      - 5432:5432


# SUBIR IMAGEN DOCKER
- Ejecutar el comando para subir la imagen:
docker-compose up
docker-compose -f docker-compose.prod.yml up -d
docker-compose -f docker-compose.mysql.yml up -p 3307:3306 --name 
mysql-docker-test -d

- correr mysql docker (DOCKER COMPOSE)
docker-compose -f docker-compose-mysql.yml up -d

- verificar contenedores activos:
docker ps

- para bajara imagen:
docker-compose -f docker-compose.prod.yml down

- Ejecutar el comando para bajar la imagen:
docker-compose stop

- Descargara DBeaver y configurar de la siguiente manera teniendo en cuenta los datos de conexión del fichero docker-compose.yaml, captura de pantalla:

