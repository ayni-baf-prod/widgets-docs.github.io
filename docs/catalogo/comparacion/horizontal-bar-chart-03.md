# Gráfico de Barras Horizontal con Progreso

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico que muestra el progreso de indicadores mediante barras horizontales, con porcentajes respecto a un presupuesto y colores que reflejan umbrales segmentados adaptados a indicadores incrementales o decrementales.
- **Identificador único**: `HORIZONAL_BAR_CHART_03`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Visualizar el avance de indicadores clave en relación con un presupuesto, destacando su desempeño mediante colores basados en umbrales específicos para indicadores incrementales (donde mayor es mejor) o decrementales (donde menor es mejor).
- **Casos de uso**:
    - Mostrar el progreso de ventas o ingresos respecto a su presupuesto (incremental).
    - Analizar el cumplimiento de costos o gastos frente a su presupuesto (decremental).
    - Evaluar el desempeño de proyectos con metas ajustadas a incrementos o reducciones.
- **Tipos de análisis soportados**: Comparativo, de progreso.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable categórica (ítem), 1 variable categórica (tipo de indicador: incremental/decremental), 1 variable numérica (porcentaje de progreso), 3 variables numéricas (umbrales para verde, amarillo, rojo).
    - Máximo: 1 variable categórica (ítem), 1 variable categórica (tipo), 5 variables numéricas (porcentajes), 3 variables numéricas (umbrales por ítem).
    - Tipos de datos: Categórico (ítems, tipo), numérico (porcentajes, umbrales).
  - **Estructura de datos** (grilla):

    | Ítem       | Tipo Indicador | Progreso (%) | Umbral Verde (%) | Umbral Amarillo (%) | Umbral Rojo (%) |
    |------------|----------------|--------------|------------------|---------------------|-----------------|
    | Sales      | Incremental    | 82           | 80               | 60                  | 40              |
    | Expenses   | Decremental    | 71           | 60               | 80                  | 100             |
    | Marketing  | Incremental    | 45           | 80               | 60                  | 40              |
    | Logistics  | Decremental    | 92           | 40               | 60                  | 80              |

  - **Notas sobre umbrales**:
      - Para indicadores incrementales, el umbral verde debe ser el mayor (ej. ≥80%), amarillo intermedio (ej. 60-79%), y rojo el menor (ej. ≤40%).
      - Para indicadores decrementales, el umbral verde debe ser el menor (ej. ≤40%), amarillo intermedio (ej. 41-60%), y rojo el mayor (ej. ≥80%).
- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: Hasta 10 ítems; recomendado 5.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Barras horizontales con longitudes proporcionales al porcentaje de progreso, alineadas a la izquierda.
    - Dimensiones: Mínimo 300x200 px, adaptable.
- **Categorías/Series**:
    - Máximo 10 ítems.
    - Exceso: Mostrar advertencia o truncar.
- **Opciones de personalización**:
    - Colores: Basados en umbrales y tipo de indicador (verde: dentro del rango óptimo, amarillo: rango de alerta, rojo: fuera de rango).
    - Etiquetas: Mostrar nombres de ítems y porcentajes de progreso.
    - Formato de valores: Porcentajes.
    - Ordenamiento: Por porcentaje (descendente) o alfabético.
    - Escalas: Lineal en eje X (0-100%).
    - Umbrales: Colores asignados dinámicamente según el tipo de indicador y los rangos definidos en los datos (verde, amarillo, rojo).
    - Casuísticas:
        - **Incremental**: Progreso ≥ Umbral Verde (verde), Umbral Amarillo ≤ Progreso < Umbral Verde (amarillo), Progreso < Umbral Rojo (rojo).
        - **Decremental**: Progreso ≤ Umbral Verde (verde), Umbral Verde < Progreso ≤ Umbral Amarillo (amarillo), Progreso > Umbral Rojo (rojo).

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar ítems específicos.
    - Tooltips: Mostrar porcentaje exacto, tipo de indicador y umbrales al pasar el cursor.
    - Zoom: No aplica.
- **Eventos soportados**: Clic en barra para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 10 ítems.
- **Casos no recomendados**: No usar para tendencias temporales (usar gráfico de líneas).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar el progreso de ítems con indicadores incrementales y decrementales.
- **Datos de entrada**:
  ```
  | Ítem       | Tipo Indicador | Progreso (%) | Umbral Verde (%) | Umbral Amarillo (%) | Umbral Rojo (%) |
  |------------|----------------|--------------|------------------|---------------------|-----------------|
  | Sales      | Incremental    | 82           | 80               | 60                  | 40              |
  | Expenses   | Decremental    | 71           | 60               | 80                  | 100             |
  | Marketing  | Incremental    | 45           | 80               | 60                  | 40              |
  | Logistics  | Decremental    | 92           | 40               | 60                  | 80              |
  ```
- **Resultado visual**: Gráfico de barras horizontales: "Sales" (82%, verde), "Expenses" (71%, amarillo), "Marketing" (45%, rojo), "Logistics" (92%, rojo). 
- **Configuración aplicada**: Colores según umbrales y tipo (incremental/decremental), formato porcentaje, orden descendente.

## 8. Requerimientos Técnicos
- **Dependencias**: Chart.js, D3.js.
- **Formato de salida**: SVG.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Asegurar que las barras sean legibles y los colores diferenciables según el tipo de indicador.
- Permitir ajuste de ancho de barras.