# Variables de entorno
CONTAINER_NAME = mysql-db-container
DB_ROOT_PASSWORD = 1234
DB_NAME = db_local
DB_PORT = 3306
DOCKER_IMAGE = mysql:latest

up:
	@echo "-> Levantando el contenedor Docker para la base de datos MySQL..."
	docker run --name $(CONTAINER_NAME) \
	-e MYSQL_ROOT_PASSWORD=$(DB_ROOT_PASSWORD) \
	-e MYSQL_DATABASE=$(DB_NAME) \
	-p $(DB_PORT):$(DB_PORT) \
	-d $(DOCKER_IMAGE)
	@echo "-> Contenedor '$(CONTAINER_NAME)' corriendo y accesible en localhost:$(DB_PORT)."

stop:
	@echo "-> Deteniendo el contenedor '$(CONTAINER_NAME)'..."
	docker stop $(CONTAINER_NAME)

start:
	@echo "-> Arrancando el contenedor detenido '$(CONTAINER_NAME)'..."
	docker start $(CONTAINER_NAME)

down: stop
	@echo "-> Eliminando el contenedor '$(CONTAINER_NAME)' y sus datos..."
	docker rm $(CONTAINER_NAME)

status:
	@echo "-> Estado del contenedor '$(CONTAINER_NAME)':"
	docker ps -a --filter name=$(CONTAINER_NAME)

shell:
	docker exec -it $(CONTAINER_NAME) /bin/bash

mysql-cli:
	docker exec -it $(CONTAINER_NAME) mysql -u root -p$(DB_ROOT_PASSWORD) $(DB_NAME)