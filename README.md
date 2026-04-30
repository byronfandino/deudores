# 📦 PROYECTO SACINV

## Entorno Docker
Sistema de inventario para papelería y miscelánea, desarrollado con **PHP 8.2**, **Apache**, **PostgreSQL** y **Node.js** usando `docker-compose`.

---

## 🚀 Requisitos previos

- Docker y Docker Compose instalados.
- Git instalado.
- No debe estar ocupado el puerto 80 👈🏻
 
---

## ⚙️ Preparación inicial

1. **Clonar el repositorio**
   ```bash
   git clone https://github.com/byronfandino/sacinv.git
   cd sacinv
   ```

2. **Ajusta permisos para PostgreSQL y ejecutar el script** *(Para distribuciones de linux)*
   > *(solo la primera vez o si cambias de computador)*
   ```bash
   sudo chmod +x ./preconfiguracion.sh
   sudo ./mi_script.sh
   ```

3. **Colocar el backup de la base de datos**
   - Actualmente ya cuenta un backup con datos de prueba llamado `backup_db.backup` dentro del directorio `backup_db/`.
   - Para importar otra base de datos con la misma estructura de tablas, el archivo debe llamarse `backup_db.backup` y ubicarla dentro del directorio `backup_db/`, ya que este directorio es un bind volume con el contenedor de postgres.

---

## ▶️ Levantar el proyecto 

1. **Construir e iniciar los contenedores**
   ```bash
   docker compose up -d --build
   ```

2. **Verificar que los contenedores estén activos**
   ```bash
   docker ps
   ```

3. **Acceder al sitio web local**
   - [http://localhost](http://localhost)

---

## 🗄️ Restaurar la base de datos del directorio `backup_db`

Para restaurar desde el backup se debe usar `pg_restore`, así:
```bash
docker exec -it postgres_db pg_restore -U bfandino -d dbdeudores ./backup_db/backup_db.backup
```
---

## 📌 Notas

- El puerto `80` está configurado para acceso local y en la red LAN.
- Si modificas permisos en los volúmenes, puedes ejecutar el script de permisos nuevamente.
- El contenedor de **Node** ejecuta automáticamente `npm install` y `gulp dev` al iniciar.
- El contenedor de **Apache** ejecuta automáticamente `composer install`.

---

## 📂 Estructura de directorios

```
sacinv/
├── backup_db/            # Archivos de respaldo de la BD
├── data-postgres/        # Datos persistentes de PostgreSQL
├── docker/               # Archivos Dockerfile y scripts
│   ├── apache/
│   └── node/
├── includes/             # Configuración PHP (app.php, database.php, etc.)
├── public/               # Carpeta pública (index.php)
├── vistas/               # Vistas del sistema
├── docker-compose.yml
├── .env                  # Variables de entorno
└── README.md
```

## Ver estructura de la base de datos

Aquí puedes ver la [estructura de la base de datos](estructura_db.md).

## Ver la clasificación de directorios

Aquí puedes ver la clasificación de directorios en views [organización en views](https://gist.github.com/byronfandino/6bf82c92eee9eeff17e895d923d55077).

### Ver HTML de marcas
Marcas [catalog-brands](https://gist.github.com/byronfandino/6d712542b393c9d9200c1ea7fbbe2be5).

### Ver HTML de categorias
Categorías [catalog-categories](https://gist.github.com/byronfandino/610d24397d72ca6bd8d4a4096d9b0f90).

### Ver HTML de tags
Tags [catalog-tags](https://gist.github.com/byronfandino/f74b3eff15b3ba3844222c4f8b0d9b0e).

