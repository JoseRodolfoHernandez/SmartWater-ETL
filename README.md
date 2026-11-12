# Smart Water – Almacenamiento y preparación de datos (Big Data)

Módulo **Smart Water (SW-01)** del proyecto Ciudad Inteligente. Universidad de Cundinamarca, Extensión Chía – Ingeniería de Sistemas y Computación (7.º semestre).

**Autores:** Sebastián Pedraza Bernal, Jose Rodolfo Hernandez
**Docente:** Edison Gustavo Cañón Varela · **Asignatura:** Big Data

## Qué contiene
| Carpeta | Contenido |
|---|---|
| `sql/` | Scripts 01 a 06 (creación, carga, validación, DW, validación ETL, consultas analíticas) |
| `simulacion/` | `simulador_smartwater.py` (semilla 701) |
| `ssis/` | Proyecto `ETL_SmartWater` con el paquete `Carga_SmartWaterDW.dtsx` |
| `datos/` | CSV generados (Medicion, Evento, Accionamiento) si el tamaño lo permite; si no, se regeneran con el simulador |
| `evidencias/` | Capturas de ejecución (opcional) |

## Requisitos
SQL Server 2022 (Developer) + SSMS · Visual Studio 2022 con SSIS · Python 3 con `numpy`.

## Cómo reproducir
1. Ejecutar el **script 01** en SSMS: crea `SmartWaterDB` y sus tablas de referencia.
2. Ejecutar `python simulacion/simulador_smartwater.py` (genera los 3 CSV, 1.008.000 mediciones, 1-abr a 27-oct-2026).
3. Ajustar la ruta de los CSV en `02_carga_simulacion.sql` y ejecutarlo (BULK INSERT con CHECK_CONSTRAINTS). Esperado: `Medicion = 1.008.000`.
4. Ejecutar el **script 03**: validaciones de cantidad, integridad y coherencia del origen.
5. Ejecutar el **script 04**: crea `SmartWaterDW` (DimFecha 365, DimHora 96; el resto vacío).
6. Abrir `ssis/ETL_SmartWater`, ajustar los dos administradores de conexión OLE DB (origen y DW) a su instancia y ejecutar `Carga_SmartWaterDW.dtsx`. Esperado: **1.008.000 extraídas = 1.007.157 cargadas + 843 rechazadas**.
7. Ejecutar `05_validacion_etl.sql` (conciliación, diferencia 0).
8. Ejecutar `06_consultas_analiticas.sql` (consultas C1–C7).

Repetir el paso 6 no genera duplicados (recarga controlada + restricción única).

## Enlaces
- Informe técnico: `Informe_SmartWater_ETL_final.pdf`
- Video: [PEGAR ENLACE]
