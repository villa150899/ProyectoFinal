# Sistema de Venta de Celulares: Novox Perú
Este proyecto es un sistema diseñado para gestionar la venta de celulares, permitiendo un control eficiente del inventario, clientes y ventas.

## Requisitos
## Lenguaje y entorno de desarrollo
- **Lenguaje**: Java (versión 21).
- **IDE**: Apache NetBeans IDE 19.

### Base de Datos
- **Gestor**: MySQL (versión 8.0 o compatible).
- **Conector JDBC**: `mysql-connector-java-8.2.0.jar`.

### Servidor
- **Servidor Local**: XAMPP 

### Otros
- **JDK**: 20
- **Configuraciones necesarias**:
  - Configurar el puerto del servidor MySQL en `3306`.
  - Establecer las credenciales de acceso a la base de datos en el archivo de configuración del proyecto.

### Sistema Operativo
- Compatible con Windows

## Instalación
1. Clona este repositorio:
   ```bash
   git clone (https://github.com/iDeathDear/ProyectoFinal.git)
   ```
2. Configura la base de datos:
   - Importa el archivo `proyectofinal.sql` en tu servidor MySQL.

3. Configura las credenciales de conexión en el archivo `config.properties` dentro del proyecto:
   ```properties
   db.url=jdbc:mysql://localhost:3306/proyectofinal
   db.user=root
   db.password=""
   ```
4. Asegúrate de que el archivo `mysql-connector-java-8.0.29.jar` esté incluido en las librerías del proyecto.
5. Ejecuta el proyecto desde Apache NetBeans.

## Uso del Sistema
1. **Inicio de sesión**:
   - Credenciales por defecto:
     - Usuario: `admin`
     - Contraseña: `admin123`.


## Estructura del Proyecto
```
📂 ProyectoFinal/
├── 📁 src/                 # Código fuente del sistema.
├── 📁 lib/                 # Librerías externas (como el conector JDBC).
├── 📁 database/            # Scripts SQL para la base de datos.
├── 📄 README.md            # Documentación del proyecto.
├── 📄 config.properties    # Archivo de configuración.
```

## Base de Datos

### Información de la Base de Datos
El sistema utiliza una base de datos configurada con el nombre `proyectofinal`. Asegúrate de importar el archivo `proyectofinal.sql` incluido en el proyecto para inicializar las tablas necesarias.

### Tablas principales
- **usuario**:
  ```sql
  CREATE TABLE usuario (
      id_usuario INT AUTO_INCREMENT PRIMARY KEY,
      nombre_usuario VARCHAR(50),
      contrasena VARCHAR(100),
      rol VARCHAR(20)
  );
  ```

- **cliente**:
  ```sql
  CREATE TABLE cliente (
      id_cliente INT AUTO_INCREMENT PRIMARY KEY,
      dni VARCHAR(20),
      nombre VARCHAR(50),
      telefono VARCHAR(20),
      email VARCHAR(100),
      sexo VARCHAR(10),
      edad INT
  );
  ```

- **producto**:
  ```sql
  CREATE TABLE producto (
      id_producto INT AUTO_INCREMENT PRIMARY KEY,
      nombre VARCHAR(100),
      marca VARCHAR(50),
      modelo VARCHAR(50),
      precio DECIMAL(10, 2),
      descripcion TEXT
  );
  ```

- **inventario**:
  ```sql
  CREATE TABLE inventario (
      id_inventario INT AUTO_INCREMENT PRIMARY KEY,
      id_producto INT,
      stock INT,
      ultima_actualizacion DATETIME,
      FOREIGN KEY (id_producto) REFERENCES producto(id_producto)
  );
  ```

- **venta**:
  ```sql
  CREATE TABLE venta (
      id_venta INT AUTO_INCREMENT PRIMARY KEY,
      id_cliente INT,
      id_usuario INT,
      fecha DATETIME,
      total DECIMAL(10, 2),
      FOREIGN KEY (id_cliente) REFERENCES cliente(id_cliente),
      FOREIGN KEY (id_usuario) REFERENCES usuario(id_usuario)
  );
  ```

- **detalleventa**:
  ```sql
  CREATE TABLE detalleventa (
      id_detalle INT AUTO_INCREMENT PRIMARY KEY,
      id_venta INT,
      id_producto INT,
      cantidad INT,
      precio_unitario DECIMAL(10, 2),
      subtotal DECIMAL(10, 2),
      FOREIGN KEY (id_venta) REFERENCES venta(id_venta),
      FOREIGN KEY (id_producto) REFERENCES producto(id_producto)
  );
  ```

- **backup**:
  ```sql
  CREATE TABLE backup (
      id_backup INT AUTO_INCREMENT PRIMARY KEY,
      fecha DATETIME,
      archivo VARCHAR(255)
  );
  ```

4. **Actualizar con el script final**:
   - Cuando el script final de la base de datos esté disponible, asegúrate de ejecutarlo para reemplazar las tablas provisionales.

## Capturas de Pantalla


### Pantalla Principal


## Contribuciones
1. Realiza un fork de este repositorio.
2. Crea una nueva rama:
   ```bash
   git checkout -b nueva-funcionalidad
   ```
3. Envía un pull request describiendo tus cambios.

## Licencia
Este proyecto está bajo la licencia MIT. Consulta el archivo `LICENSE` para más detalles.
