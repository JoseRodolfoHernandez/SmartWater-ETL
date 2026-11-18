# Smart Water · Módulo de agua de Ciudad Inteligente

Proyecto de Big Data (7.º semestre, Ingeniería de Sistemas y Computación, Universidad de Cundinamarca, Extensión Chía).
Integrantes: Sebastián Pedraza Bernal · Jose Rodolfo Hernandez.

**Sitio web del proyecto:** https://joserodolfohernandez.github.io/SmartWater-ETL/

## Contenido
| Carpeta | Qué contiene |
|---|---|
| `index.html` | Sitio web del PGC (problema, solución, datos, dashboard, conocimientos, decisiones, validación) |
| `sql/` | Scripts 01 a 06: modelo relacional, carga, validación, Data Warehouse en estrella, validación del ETL y consultas analíticas |
| `simulador/` | `simulador_smartwater.py`: genera 1.008.000 mediciones de 10 dispositivos (semilla 701) |
| `ssis/` | Proyecto de Integration Services (`Carga_SmartWaterDW.dtsx`) |
| `powerbi/` | Informe de Power BI (`SmartWater.pbix`) |
| `documentos/` | Informe técnico |
| `evidencias/` | Capturas del dashboard |

## Cómo reproducirlo
1. Ejecutar en SQL Server los scripts `sql/01` a `sql/06` en orden.
2. Correr `python simulador/simulador_smartwater.py` para generar Medicion, Evento y Accionamiento (CSV).
3. Abrir `ssis/ETL_SmartWater.sln` en Visual Studio y ejecutar `Carga_SmartWaterDW.dtsx` para cargar `SmartWaterDW`.
4. Abrir `powerbi/SmartWater.pbix` y conectar al Data Warehouse.

## Cifras de control
1.008.000 mediciones extraídas = 1.007.157 cargadas + 843 rechazadas · 1.735 eventos en el DW · 492,3 m³ bombeados.
