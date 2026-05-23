# Nexus Marketplace - Proyecto Final Bases de Datos 2

Este repositorio contiene los scripts y documentos de soporte para el proyecto final de **Nexus Marketplace**. Incluye una parte no relacional en MongoDB y una parte relacional/PLSQL en Oracle.

La base de datos no relacional en MongoDB almacena informacion flexible o semiestructurada de productos:

- Resenas y valoraciones de productos.
- Comentarios de clientes.
- Especificaciones tecnicas variables.
- Caracteristicas adicionales por categoria.

La base de datos propuesta se llama `nexus_marketplace_nosql`.

## Motores incluidos

- MongoDB Community Server para la base NoSQL.
- Oracle Database para scripts SQL y PL/SQL.

## Scripts Oracle SQL y PL/SQL

Los scripts Oracle se encuentran en `scripts/oracle/` y fueron integrados desde el repositorio `tef333/oracle-sql-scripts`.

Incluyen:

- Consultas SQL sobre esquema HR: joins, agrupaciones, filtros, funciones y jerarquias.
- Bloques anonimos PL/SQL: variables, ciclos, condicionales y cursores.
- Procedimientos almacenados y permisos.
- Triggers DML y manejo de excepciones.
- Taller final con ajuste salarial, validaciones, auditoria, savepoint y enfoque ACID.

Guia documental: `docs/oracle-sql-plsql.md`.

## Patrones de diseno seleccionados

Se usan dos patrones del catalogo de MongoDB:

1. **Patron de Atributo**
   - Se aplica en `productos_flexibles.especificaciones`.
   - Convierte especificaciones variables en una lista de atributos consultables:
     `{ nombre, valor, unidad, tipo }`.
   - Es adecuado porque un celular, un portatil y un accesorio no tienen exactamente los mismos campos tecnicos.

2. **Patron de Subconjunto**
   - Se aplica en `productos_flexibles.resumenResenas` y `productos_flexibles.ultimasResenas`.
   - El producto conserva solo informacion frecuente y pequena de resenas.
   - Las resenas completas quedan en la coleccion `resenas`.
   - Es adecuado porque las resenas pueden crecer mucho con el tiempo.

Referencia: https://www.mongodb.com/blog/post/building-with-patterns-a-summary-es

## Instalacion local en Ubuntu

MongoDB 8.0 Community Edition soporta Ubuntu 24.04 LTS, 22.04 LTS y 20.04 LTS de 64 bits. Primero valida tu version:

```bash
cat /etc/lsb-release
```

Instala dependencias:

```bash
sudo apt-get update
sudo apt-get install -y gnupg curl
```

Importa la llave publica de MongoDB:

```bash
curl -fsSL https://pgp.mongodb.com/server-8.0.asc | \
  sudo gpg -o /usr/share/keyrings/mongodb-server-8.0.gpg \
  --dearmor
```

Crea el repositorio segun tu version de Ubuntu.

Ubuntu 24.04:

```bash
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-8.0.gpg ] https://repo.mongodb.org/apt/ubuntu noble/mongodb-org/8.0 multiverse" | \
  sudo tee /etc/apt/sources.list.d/mongodb-org-8.0.list
```

Ubuntu 22.04:

```bash
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-8.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/8.0 multiverse" | \
  sudo tee /etc/apt/sources.list.d/mongodb-org-8.0.list
```

Ubuntu 20.04:

```bash
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-8.0.gpg ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/8.0 multiverse" | \
  sudo tee /etc/apt/sources.list.d/mongodb-org-8.0.list
```

Instala MongoDB:

```bash
sudo apt-get update
sudo apt-get install -y mongodb-org
```

Inicia el servicio:

```bash
sudo systemctl start mongod
sudo systemctl enable mongod
sudo systemctl status mongod
```

Prueba la conexion:

```bash
mongosh
```

## Ejecucion de scripts MongoDB

Desde la carpeta del proyecto:

```bash
mongosh < scripts/01_setup.mongodb.js
mongosh < scripts/02_crud.mongodb.js
mongosh < scripts/03_consultas_complejas.mongodb.js
mongosh < scripts/04_agregaciones.mongodb.js
```

Tambien puedes ejecutar un script especifico indicando la base:

```bash
mongosh "mongodb://localhost:27017/nexus_marketplace_nosql" scripts/03_consultas_complejas.mongodb.js
```

## Estructura

```text
.
|-- README.md
|-- docs/
|   |-- diseno-documental.md
|   |-- oracle-sql-plsql.md
|   `-- plan-commits.md
`-- scripts/
    |-- oracle/
    |   |-- 01_consultas_sql/
    |   |-- 02_plsql_anonimos/
    |   |-- 03_procedimientos/
    |   |-- 04_triggers_excepciones/
    |   `-- 05_taller_final/
    |-- 01_setup.mongodb.js
    |-- 02_crud.mongodb.js
    |-- 03_consultas_complejas.mongodb.js
    `-- 04_agregaciones.mongodb.js
```

## Comandos Git sugeridos

```bash
git init
git add README.md docs/diseno-documental.md
git commit -m "docs: definir diseno documental nosql"

git add scripts/01_setup.mongodb.js
git commit -m "feat: agregar carga inicial e indices mongodb"

git add scripts/02_crud.mongodb.js
git commit -m "feat: documentar operaciones crud"

git add scripts/03_consultas_complejas.mongodb.js scripts/04_agregaciones.mongodb.js docs/plan-commits.md
git commit -m "feat: agregar consultas complejas y agregaciones"
```

Para subirlo a GitHub:

```bash
git branch -M main
git remote add origin https://github.com/tef333/Proyecto-final-DB2.git
git push -u origin main
```
