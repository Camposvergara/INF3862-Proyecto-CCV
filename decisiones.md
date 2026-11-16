# Registro de decisiones

| # | Fecha | Decisión | Alternativas consideradas | Motivo | Entrega en que cambió |
|---|---|---|---|---|---|
| 1 | 2026-11-15 | Caso de uso: recomendar recetas según la actividad física del día | Balance calórico, predicción de abandono, predicción de calificación | Usa todas las fuentes (reloj, comidas, recetas y reseñas) y apoya una decisión concreta de producto | — |
| 2 | 2026-11-15 | Unidad de análisis principal: una fila por comida registrada (`fact_comida`) | Usuario-día, usuario-receta | Conecta la actividad previa con la receta elegida, que es lo que el recomendador necesita aprender | — |
| 3 | 2026-11-15 | Base relacional para la operación; series de tiempo para mediciones recientes; clave-valor para las recomendaciones | Todo en una sola base relacional | Cada patrón de acceso es distinto: transacciones, escritura masiva por tiempo y lectura por clave en milisegundos | — |
| 4 | 2026-11-15 | Almacenamiento analítico en Lakehouse (tablas Delta, capas raw/silver/gold) | Data Warehouse, Data Lake sin tablas ACID | Hay JSON de dos formatos y texto libre, y se necesita `MERGE` para corregir registros atrasados y duplicados | — |
| 5 | 2026-11-15 | Raw en schema-on-read; esquema fijo en silver | Validar el esquema al recibir | Los dos modelos de reloj usan nombres y formatos distintos (`fc`/`frecuencia_cardiaca`, epoch ms/ISO); no quiero perder datos si aparece un campo nuevo | — |
| 6 | 2026-11-15 | Particionar mediciones y hechos por fecha de medición, no de recepción | Fecha de recepción (como vienen los archivos) | Las consultas filtran por el día de la actividad; los lotes llegan hasta ~7 h tarde (p95 de 3,3 h) | — |
| 7 | 2026-11-15 | Deduplicar mediciones por (`device_id`, `ts_medicion`) | Eliminar solo filas idénticas | En la muestra, la mayoría de las repeticiones llega en otro lote con distinta hora de recepción | — |
| 8 | 2026-11-15 | Calorías del día en vivo con un acumulador por usuario y día | Calcularlo sobre el lakehouse o sumando mediciones en la base operacional | Es una consulta de frontera: agrega, pero la app la pide al instante para un solo usuario | — |
