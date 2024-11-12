
# PersonApp - Instrucciones de Uso

Este proyecto utiliza Spring Boot, Docker, MongoDB, MariaDB y Swagger para crear una aplicación modular con servicios CLI y REST. Sigue estas instrucciones para construir y ejecutar el proyecto.

---

## **Pasos para iniciar el proyecto**

### 1. **Construir el proyecto con Maven**
Ejecuta el siguiente comando en la raíz del proyecto para compilar y generar los artefactos necesarios:

```bash
mvn clean install
```

---

### 2. **Construir las imágenes Docker**
Una vez generado el proyecto, construye las imágenes Docker ejecutando:

```bash
docker-compose build --no-cache
```

El uso de `--no-cache` asegura que las imágenes sean creadas desde cero.

---

### 3. **Levantar los contenedores**
Inicia todos los servicios (MongoDB, MariaDB, CLI y REST) con el siguiente comando:

```bash
docker-compose up -d
```

---

## **Comportamiento esperado**
- **MongoDB y MariaDB**: Se levantarán primero.
- **CLI y REST**: Es probable que estos servicios fallen varias veces al inicio, ya que esperan que MongoDB y MariaDB estén completamente operativos. Docker se encargará de reiniciarlos automáticamente hasta que las conexiones sean exitosas.
- Una vez estabilizado, todos los servicios estarán en funcionamiento.

---

## **Probar los servicios**

### 1. **REST Service**
El servicio REST se puede probar abriendo el siguiente enlace en tu navegador:

```plaintext
http://localhost:3000/swagger-ui.html
```

Ahí encontrarás la interfaz de Swagger para interactuar con las API.

---

### 2. **CLI Service**
Para interactuar con el servicio CLI, ejecuta el siguiente comando para acceder al contenedor:

```bash
docker exec -it lab2grupo6-cli-service-1 sh
```

Esto abrirá una terminal dentro del contenedor. Luego, ejecuta el comando:

```bash
java -jar cli-input-adapter.jar
```

Esto iniciará el menú interactivo del CLI. Sigue las opciones disponibles en el menú para probar las funcionalidades.

---

## **Notas Importantes**
- Si REST o CLI no funcionan al primer intento, verifica los logs de los contenedores con:

```bash
docker logs <nombre_del_contenedor>
```

Reemplaza `<nombre_del_contenedor>` con `lab2grupo6-rest-service-1` o `lab2grupo6-cli-service-1`.

- Para detener los servicios, utiliza:

```bash
docker-compose down
```

Esto eliminará los contenedores pero conservará los volúmenes de datos para MongoDB y MariaDB. 

¡Disfruta trabajando con PersonApp! 🚀
