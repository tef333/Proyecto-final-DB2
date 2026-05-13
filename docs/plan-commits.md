# Plan de commits para GitHub

La idea es que el repositorio evidencie el avance del proyecto en pasos claros.

## Commit 1

```bash
git add README.md docs/diseno-documental.md
git commit -m "docs: definir diseno documental nosql"
```

Contenido:

- Objetivo de la base NoSQL.
- Justificacion de MongoDB.
- Colecciones principales.
- Patrones de diseno seleccionados.

## Commit 2

```bash
git add scripts/01_setup.mongodb.js
git commit -m "feat: agregar carga inicial e indices mongodb"
```

Contenido:

- Creacion de colecciones.
- Insercion de datos de ejemplo.
- Indices para consultas frecuentes.

## Commit 3

```bash
git add scripts/02_crud.mongodb.js
git commit -m "feat: documentar operaciones crud"
```

Contenido:

- Inserciones.
- Consultas.
- Actualizaciones.
- Eliminaciones logicas y fisicas.

## Commit 4

```bash
git add scripts/03_consultas_complejas.mongodb.js scripts/04_agregaciones.mongodb.js docs/plan-commits.md
git commit -m "feat: agregar consultas complejas y agregaciones"
```

Contenido:

- Consultas con filtros combinados.
- Busqueda textual.
- Pipelines de agregacion.
- Recalculo de resumenes de resenas.

## Creacion del repositorio remoto

Opcion con GitHub CLI:

```bash
gh repo create tienda-nosql-mongodb --public --source=. --remote=origin --push
```

Opcion manual:

1. Crear un repositorio vacio en GitHub llamado `tienda-nosql-mongodb`.
2. Ejecutar:

```bash
git branch -M main
git remote add origin https://github.com/TU_USUARIO/tienda-nosql-mongodb.git
git push -u origin main
```

