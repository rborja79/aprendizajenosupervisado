# Patrones invisibles: información, incertidumbre y movilidad urbana

Proyecto Retador · **Aprendizaje de Máquina No Supervisado** · Universidad de La Sabana · 2026-II
Consultoría analítica para **UrbanMove** sobre NYC Taxi Trip Duration (1.458.644 viajes, enero–junio de 2016).

## Equipo


| Integrante          | Código    | Bloque técnico                        |
| ------------------- | ---------- | -------------------------------------- |
| Ricardo Borja       | 0000333542 | Rol 1 · Incertidumbre e información  |
| Gabriel Murillo     | 0000285035 | Rol 2 · Segmentación por partición  |
| Samuel Robayo       | 0000329495 | Rol 3 · Mezclas y variables latentes  |
| Maria Andrea Torres | 0000334682 | Rol 4 · Negocio y selección de datos |

## Contenido del repositorio


| Archivo                           | Qué es                                                                     |
| --------------------------------- | --------------------------------------------------------------------------- |
| `AnalisisTaxiTrip.ipynb`          | Cuaderno completo, ejecutado y comentado. Es la fuente de todas las cifras. |
| `Documento_Soporte_UrbanMove.pdf` | Documento de soporte con resultados y recomendaciones.                      |
| `UrbanMove.pdf`                   | Presentación.                                                              |
| `Video_Soporte_UrbanMove.mp4`     | Sustentación en video.                                                     |

No se versionan ni los datos de entrada (331 MB) ni las figuras: los primeros se descargan de las
fuentes de abajo y las segundas se regeneran solas al ejecutar el cuaderno.

## Cómo reproducirlo

```bash
pip install pandas numpy scikit-learn geopandas pyproj geopy holidays matplotlib jupyter
# Descargar el dataset y el shapefile (enlaces abajo) en:
#   nyc-taxi-trip-duration/train.csv
#   taxi_zones/
jupyter nbconvert --to notebook --execute AnalisisTaxiTrip.ipynb --inplace
```

El cuaderno corre de principio a fin en **menos de dos minutos**. La distancia geodésica WGS84 se
resuelve vectorizada con `pyproj.Geod` y el propio cuaderno la contrasta contra `geopy` sobre una
muestra de 2.000 viajes: la diferencia máxima es del orden de 1e-12 km, así que es la misma
geodésica, no una aproximación.

**Semilla única 2026** en muestreo, K-means, DBSCAN y EM. Los resultados son reproducibles.

## Fuentes de datos

- Dataset: https://www.kaggle.com/c/nyc-taxi-trip-duration/data
- Shapefile de zonas de taxi de NYC: https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page
