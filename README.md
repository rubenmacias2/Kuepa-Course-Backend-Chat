#Proyecto -  Kuepa Course Backend Chat

servicio backend con chat en tiempo real para prueba tecnica Kuepa 

## Instalación

Para instalar todas las dependencias necesarias, ejecuta el siguiente comando:

```bash
npm install
```

O, alternativamente:

```bash
npm i
```

### Dependencias

Estas son algunas de las dependencias que se instalarán:

- cors
- dotenv
- express
- morgan
- mysql2
- nodemon
- sequelize
- socket.io

## Uso

Para iniciar el servidor, utiliza el siguiente comando:

```bash
npm start
```

Luego, abre tu navegador y ve a `http://localhost:8081`.


## Configuración

Asegúrate de que tu aplicación esté configurada para usar el puerto correcto. En este caso, el servidor está configurado para ejecutarse en `http://localhost:8080`.


### Variables de Entorno

El archivo `.env` es esencial para configurar las variables necesarias para la conexión a la base de datos y el servidor. Asegúrate de incluir las siguientes variables en tu archivo `.env`:

```env
DBHOST='bmgjxray9a9sqlmo6mrs-mysql.services.clever-cloud.com'
DBNAME='bmgjxray9a9sqlmo6mrs'
DBUSER='uxkkmgmy7siqfknp'
DBPASSWORD='SFQJowqFS8qbmOlLuu0g'
DBPORT=3306
PORT=8081
REACT_APP_API_URL=http://localhost:8081
```

Estas variables se utilizan para conectar tu aplicación a la base de datos y para establecer el puerto en el que se ejecutará el servidor. La base de datos está alojada en un servicio gratuito llamado Clever Cloud, al que se accede con las credenciales especificadas en el archivo `.env`.


### Script para la Base de Datos

Para garantizar que la base de datos pueda manejar emojis, ejecuta los siguientes comandos para cambiar la codificación:

```sql
ALTER DATABASE bmgjxray9a9sqlmo6mrs CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci;
ALTER TABLE bmgjxray9a9sqlmo6mrs.MENSAJE CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
ALTER TABLE bmgjxray9a9sqlmo6mrs.MENSAJE MODIFY contenido VARCHAR(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

### Script para Crear Tablas

```sql
USE bmgjxray9a9sqlmo6mrs;

CREATE TABLE USUARIO (
    nombreUsuario VARCHAR(100) NOT NULL PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    contrasena VARCHAR(100) NOT NULL,
    rol VARCHAR(50) NOT NULL
);

CREATE TABLE MENSAJE (
    id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    contenido VARCHAR(100) NOT NULL,
    fecha VARCHAR(100) NOT NULL,
    usuario VARCHAR(50) NOT NULL,
    FOREIGN KEY (usuario) REFERENCES USUARIO(nombreUsuario)
);
```

## Contribuciones

Si deseas contribuir a este proyecto, por favor sigue los siguientes pasos:

1. Haz un fork del repositorio.
2. Crea una nueva rama (`git checkout -b feature/nueva-feature`).
3. Realiza tus cambios y haz commit (`git commit -am 'Agrega nueva feature'`).
4. Sube tus cambios (`git push origin feature/nueva-feature`).
5. Abre un Pull Request.

