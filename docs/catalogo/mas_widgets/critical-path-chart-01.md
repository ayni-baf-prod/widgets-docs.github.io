# Gráfico Gannt de Camino Crítico

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de barras horizontales que muestra el cronograma de tareas, destacando el camino crítico (tareas que determinan la duración total) con indicadores de duración.
- **Identificador único**: `CRITICAL_PATH_CHART_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Identificar y visualizar las tareas críticas que impactan la fecha de finalización de un proyecto o proceso, facilitando la gestión de recursos y tiempos.
- **Casos de uso**: 
  - Monitorear el camino crítico en cronogramas de proyectos.
  - Identificar cuellos de botella en flujos de producción en operaciones.
  - Analizar etapas críticas en campañas de marketing en comercial.
  - Evaluar actividades clave en cierres financieros en finanzas.
- **Tipos de análisis soportados**: Temporal, planificación.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
  - Número mínimo y máximo de variables: 1 variable categórica (tareas), 2 variables temporales (inicio, fin) y 2 variables numéricas
  - Tipos de datos soportados: Categórico (tareas), temporal (fechas/días) y numérico (entero)
  - Estructura de datos: Ejemplo en formato de grilla:

    | Task    | Task Start Date | Task Due Date | Task Duration Days | Task Overdue Days |
    |---------|-----------------|---------------|--------------------|-------------------|
    | Task 1  | 01/01/2023      | 01/02/2023    | 2                  | 5                 |
    | Task 2  | 01/03/2023      | 01/09/2023    | 6                  | 1                 |
    | Task 3  | 01/10/2023      | 01/15/2023    | 5                  | 0                 |
    | Task 4  | 01/16/2023      | 01/30/2023    | 12                 | 7                 |
    | Task 5  | 02/01/2023      | 03/14/2023    | 31                 | 0                 |
    | Task 6  | 02/15/2023      | 03/14/2023    | 21                 | 2                 |
    | Task 7  | 03/15/2023      | 03/30/2023    | 13                 | 1                 |
    | Task 8  | 04/01/2023      | 04/14/2023    | 11                 | 6                 |
    | Task 9  | 04/01/2023      | 04/14/2023    | 11                 | 6                 |
    | Task 10 | 03/01/2023      | 03/09/2023    | 8                  | 6                 |

- **Fuente de datos**: Tablas SQL desde un datawarehouse (ej. tabla de cronogramas con identificación de camino crítico).
- **Volumen de datos**: Hasta 50 tareas; recomendado 10-20 tareas.

## 4. Configuración Visual
- **Estructura del gráfico**:
  - Barras horizontales que representan la duración de tareas, con resaltado especial (ej. color rojo) para tareas críticas.
  - Dimensiones recomendadas: 500x300 px, adaptable.
- **Categorías/Series**:
  - Número máximo de tareas: 50.
  - Comportamiento con exceso de tareas: Mostrar desplazamiento o paginación.
- **Opciones de personalización**:
  - Colores: Configurables por crítico (ej. rojo para crítico, azul para no crítico) y estado (verde completado, naranja retrasado).
  - Etiquetas: Mostrar nombres de tareas y fechas en tooltips, opcionalmente en barras.
  - Escalas: Eje X (días o fechas), eje Y (tareas).
  - Líneas de referencia: Opcional para fechas clave (ej. fecha actual, fin proyectado).

## 5. Interactividad
- **Funcionalidades interactivas**:
  - Filtros: Seleccionar rango temporal o mostrar solo tareas críticas.
  - Tooltips: Mostrar detalles (inicio, fin, estado, crítico) al pasar el cursor.
  - Zoom: En eje X para rangos temporales largos.
- **Eventos soportados**: Clic en barra para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 50 tareas.
- **Casos no recomendados**: No usar para datos no temporales (usar gráfico de barras).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar el camino crítico de un proyecto.
- **Datos de entrada**:
  ```
  | Task    | Task Start Date | Task Due Date | Task Duration Days | Task Overdue Days |
  |---------|-----------------|---------------|--------------------|-------------------|
  | Task 1  | 01/01/2023      | 01/02/2023    | 2                  | 5                 |
  | Task 2  | 01/03/2023      | 01/09/2023    | 6                  | 1                 |
  | Task 3  | 01/10/2023      | 01/15/2023    | 5                  | 0                 |
  | Task 4  | 01/16/2023      | 01/30/2023    | 12                 | 7                 |
  | Task 5  | 02/01/2023      | 03/14/2023    | 31                 | 0                 |
  | Task 6  | 02/15/2023      | 03/14/2023    | 21                 | 2                 |
  | Task 7  | 03/15/2023      | 03/30/2023    | 13                 | 1                 |
  | Task 8  | 04/01/2023      | 04/14/2023    | 11                 | 6                 |
  | Task 9  | 04/01/2023      | 04/14/2023    | 11                 | 6                 |
  | Task 10 | 03/01/2023      | 03/09/2023    | 8                  | 6                 |
  | Task 11 | 03/10/2023      | 03/11/2023    | 2                  | 1                 |
  | Task 12 | 03/12/2023      | 03/16/2023    | 5                  | 5                 |
  | Task 13 | 03/17/2023      | 04/03/2023    | 13                 | 0                 |
  | Task 14 | 04/04/2023      | 04/14/2023    | 10                 | 6                 |
  | Task 15 | 04/15/2023      | 04/30/2023    | 11                 | 2                 |
  | Task 16 | 05/02/2023      | 05/30/2023    | 22                 | 5                 |
  | Task 17 | 05/31/2023      | 06/14/2023    | 12                 | 4                 |
  | Task 18 | 06/15/2023      | 07/05/2023    | 16                 | 4                 |
  | Task 19 | 02/15/2023      | 02/20/2023    | 5                  | 7                 |
  | Task 20 | 02/20/2023      | 03/11/2023    | 16                 | 4                 |
  | Task 21 | 03/12/2023      | 04/17/2023    | 27                 | 5                 |
  | Task 22 | 04/18/2023      | 05/03/2023    | 13                 | 0                 |
  | Task 23 | 05/04/2023      | 05/14/2023    | 8                  | 2                 |
  | Task 24 | 05/15/2023      | 05/31/2023    | 14                 | 2                 |
  | Task 25 | 06/02/2023      | 06/15/2023    | 11                 | 6                 |
  | Task 26 | 06/17/2023      | 06/19/2023    | 2                  | 4                 |
  | Task 27 | 06/20/2023      | 06/21/2023    | 3                  | 3                 |
  ```
- **Resultado visual**: 
  - Gráfico de barras horizontales: Tarea 1 (rojo), Tarea 2 (azul), Tarea 3 (rojo), Tarea 4 (azul).
  - Eje X: Day 50 a Day 350.

- **Configuración aplicada**: Rojo para crítico, azul para no crítico, escala en días.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 370px; position: relative;">
  <iframe src="../../../assets/widgets_html/mas/critical_path_chart_01_interactive.html" 
          style="width: 100%; height: 370px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo de Critical Path Chart">
  </iframe>
</div>

## 8. Requerimientos Técnicos
- **Formato de salida**: Canvas.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo (móvil, desktop).

## 9. Notas Adicionales
- Asegurar legibilidad de resaltados en tareas críticas.
- Considerar integración con alertas para retrasos en el camino crítico.