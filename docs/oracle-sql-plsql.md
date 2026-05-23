# Scripts Oracle SQL y PL/SQL

## Objetivo

Esta seccion documenta los scripts Oracle integrados al proyecto final de Nexus Marketplace. Estos archivos complementan la base NoSQL en MongoDB con practicas relacionales, consultas SQL, programacion PL/SQL, procedimientos almacenados, triggers, excepciones y manejo transaccional.

Los scripts fueron integrados desde el repositorio:

```text
https://github.com/tef333/oracle-sql-scripts
```

## Estructura integrada

```text
scripts/oracle/
|-- 01_consultas_sql/
|   `-- 01_consultas_hr.sql
|-- 02_plsql_anonimos/
|   `-- 02_bloques_anonimos.sql
|-- 03_procedimientos/
|   `-- 03_procedimientos.sql
|-- 04_triggers_excepciones/
|   `-- 04_triggers_excepciones.sql
`-- 05_taller_final/
    `-- Taller_SLQ_1Estefania_Paredes_Santiago_Rojas.sql
```

## Descripcion por bloque

### 1. Consultas SQL

Archivo:

```text
scripts/oracle/01_consultas_sql/01_consultas_hr.sql
```

Incluye consultas sobre el esquema `HR` de Oracle. Demuestra:

- `LEFT JOIN`.
- `GROUP BY`.
- `HAVING`.
- Funciones de cadena como `LPAD`, `SUBSTR` e `INITCAP`.
- Jerarquias de empleados mediante self-join.
- Filtros por region, salario y cargo.

### 2. Bloques anonimos PL/SQL

Archivo:

```text
scripts/oracle/02_plsql_anonimos/02_bloques_anonimos.sql
```

Demuestra el uso de:

- Variables.
- Condicionales.
- Ciclos.
- Cursores.
- Bloques `DECLARE`, `BEGIN` y `END`.

### 3. Procedimientos almacenados

Archivo:

```text
scripts/oracle/03_procedimientos/03_procedimientos.sql
```

Incluye procedimientos almacenados con parametros y gestion de permisos. Este bloque evidencia programacion dentro de la base de datos y reutilizacion de logica.

### 4. Triggers y excepciones

Archivo:

```text
scripts/oracle/04_triggers_excepciones/04_triggers_excepciones.sql
```

Incluye:

- Triggers `BEFORE` y `AFTER`.
- Eventos DML.
- Manejo de excepciones con `WHEN OTHERS`.
- Excepciones definidas por el usuario.

### 5. Taller final Oracle

Archivo:

```text
scripts/oracle/05_taller_final/Taller_SLQ_1Estefania_Paredes_Santiago_Rojas.sql
```

Este script desarrolla un caso de ajuste salarial con:

- Consultas diagnosticas.
- CTEs.
- Validacion de empleados elegibles.
- Actualizacion controlada.
- Uso de `SAVEPOINT`.
- Auditoria en tabla de log.
- Validacion posterior.
- Aplicacion de propiedades ACID.

## Ejecucion sugerida

Los scripts pueden ejecutarse desde Oracle SQL Developer, SQLcl o SQL*Plus.

Ejemplo con SQLcl o SQL*Plus:

```sql
@scripts/oracle/01_consultas_sql/01_consultas_hr.sql
@scripts/oracle/02_plsql_anonimos/02_bloques_anonimos.sql
@scripts/oracle/03_procedimientos/03_procedimientos.sql
@scripts/oracle/04_triggers_excepciones/04_triggers_excepciones.sql
@scripts/oracle/05_taller_final/Taller_SLQ_1Estefania_Paredes_Santiago_Rojas.sql
```

## Relacion con Nexus Marketplace

La parte Oracle demuestra el componente relacional y transaccional de Bases de Datos 2. La parte MongoDB demuestra el componente NoSQL para informacion flexible.

En conjunto, el repositorio evidencia:

- Modelo relacional y consultas SQL.
- Logica procedural en PL/SQL.
- Triggers, excepciones y auditoria.
- Manejo transaccional.
- Diseno documental NoSQL.
- CRUD, consultas complejas y agregaciones en MongoDB.

