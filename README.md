# Datos

Los datos no se versionan en este repositorio. Se obtienen desde Canvas (curso INF3862,
sección del proyecto) y se ubican localmente así:

```
datos/
  recipes.parquet
  reviews.parquet
  wearable/
    dispositivos.csv
    sesiones.jsonl
    comidas.csv
    mediciones/AAAA-MM-DD/HH.jsonl.gz
```

| Fuente | Contenido |
|---|---|
| `recipes.parquet` | 522.517 recetas de Food.com (Kaggle, licencia CC0) |
| `reviews.parquet` | 1.401.982 reseñas de 271.907 usuarios |
| `dispositivos.csv` | 315 relojes vinculados a 300 usuarios |
| `sesiones.jsonl` | 4.840 sesiones de actividad (16-12-2007 a 14-02-2008) |
| `comidas.csv` | 22.106 comidas registradas desde la app |
| `mediciones/` | Mediciones del reloj, agrupadas por día y hora de recepción |

Todas las fechas del wearable están en UTC. La hora local se obtiene con `zona_horaria`
de `dispositivos.csv`.

La muestra que se usará en la E2 (usuarios y semanas seleccionados) se documentará aquí.
