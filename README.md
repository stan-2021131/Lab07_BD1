# Lab 7 - Visualización de Datos

## Descripción

Este proyecto corresponde al Laboratorio 7 del curso CC3088 - Bases de Datos.

El objetivo es implementar un ambiente reproducible utilizando Docker Compose con:

* PostgreSQL como base de datos principal.
* Metabase como herramienta de visualización y análisis.
* Persistencia completa de dashboards y configuraciones.
* Carga automática de scripts SQL.

Todo el entorno debe levantarse únicamente ejecutando:

```bash
docker compose up
```

---

## Estructura del proyecto

```txt
Lab7/
│
├── data/
│   ├── DDL.sql
│   └── DATA.sql
│
├── postgres-init/
│   └── 01-init.sql
│
├── metabase-data/
│
├── .env.example
├── docker-compose.yml.example
├── README.md
└── .gitignore
```

---

## Requisitos

* Docker
* Docker Compose

Verificar instalación:

```bash
docker --version
docker compose version
```

---

## Informe
El informe de los indicadores realizados para el laboratorio se encuentran en `./documentation/Laboratorio 7.pdf`. En él se detalla:
1. Nombre del indicador. 
2. Qué representa en términos de negocio. 
3. Por qué es importante para el área. 
4. Qué tipo de visualización se usó y por qué es la más adecuada. 
5. La consulta SQL completa usada para generarlo en Metabase.

## Configuración inicial

### 1. Crear archivo `.env`

Copiar el archivo de ejemplo:

```bash
cp .env.example .env
```

---

### 2. Crear archivo `docker-compose.yml`

Copiar el archivo de ejemplo:

```bash
cp docker-compose.yml.example docker-compose.yml
```

---

## Levantar el proyecto

Ejecutar:

```bash
docker compose up
```

Para ejecutar en background:

```bash
docker compose up -d
```

---

## Servicios

### PostgreSQL

* Host: localhost
* Puerto: 5432
* Base de datos: retailmax

### Metabase

* URL: http://localhost:3000

---

## Credenciales PostgreSQL

```txt
Database: retailmax
User: demo
Password: demo123
```

---

## Credenciales Metabase para calificación

```txt
Correo: calificar@uvg.edu.gt
Contraseña: secret123+
```

---

## Persistencia

### PostgreSQL

La información de PostgreSQL se almacena en un volumen Docker:

```txt
postgres_data
```

---

### Metabase

Toda la configuración de Metabase se almacena en:

```txt
metabase-data/
```

Esto incluye:

* Dashboards
* Preguntas SQL
* Usuarios
* Configuración
* Visualizaciones

---

## Carga automática de SQL

Al iniciar el contenedor de PostgreSQL se ejecutan automáticamente:

```txt
data/DDL.sql
data/DML.sql
```

Esto ocurre mediante:

```txt
postgres-init/01-init.sql
```

---

## Trabajo colaborativo

Antes de hacer pull del repositorio se recomienda detener los contenedores:

```bash
docker compose down
```

Luego actualizar:

```bash
git pull
```

Y finalmente levantar nuevamente:

```bash
docker compose up
```

---

## Reiniciar completamente el entorno

Eliminar contenedores y volúmenes:

```bash
docker compose down -v
```

Luego levantar nuevamente:

```bash
docker compose up
```

---

## Notas importantes

* Los dashboards deben construirse únicamente usando SQL nativo en Metabase.
* No se permite el constructor visual.
* La carpeta `metabase-data/` debe mantenerse en el repositorio para conservar los dashboards.

---

## Integrantes
