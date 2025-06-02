# Gráfico de Barras Verticales de comparación

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de barras verticales que compara dos métricas (ej. presupuesto gastado y planificado), destacando desviaciones.
- **Identificador único**: `VERTICAL_BAR_CHART_02`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Comparar dos valores numéricos (ej. ejecutado vs. planificado) para identificar los ítems con mayor y menor desempeño, facilitando la detección de desviaciones.
- **Casos de uso**: 
  - Identificar los proyectos con mayor y menor desviación entre presupuesto gastado y planificado.
  - Analizar el rendimiento financiero de productos o regiones en términos de ejecución vs. planificación.
  - Monitorear extremos en métricas operativas (ej. horas trabajadas vs. estimadas) en contextos como proyectos o producción.
- **Tipos de análisis soportados**: Comparativo, descriptivo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
  - Número mínimo y máximo de variables: 1 variable categórica (ítem), 2 variables numéricas (valor ejecutado, valor planificado).
  - Tipos de datos soportados: Categórico (ítem), numérico (valores).
  - Estructura de datos: Ejemplo en formato de grilla:
    ```
    | Ítem       | Budget Spent | Budget Planned |
    |------------|--------------|----------------|
    | Project 1  | $1000        | $800           |
    | Project 2  | $800         | $900           |
    | Project 3  | $500         | $600           |
    | Project 4  | $250         | $300           |
    | Project 5  | $0           | $250           |
    ```
- **Fuente de datos**: Tablas SQL desde un datawarehouse (ej. tabla de presupuestos y ejecución).
- **Volumen de datos**: Límite recomendado de 5 ítems; máximo de 10 ítems antes de requerir ajuste.

## 4. Configuración Visual
- **Estructura del gráfico**:
  - Barras verticales agrupadas por ítem, con dos barras por ítem (ej. Budget Spent, Budget Planned).
  - Colores indicadores: Azul (Budget Spent), Verde (Budget Planned), configurables.
  - Dimensiones recomendadas: 400x300 px, adaptable.
- **Categorías/Series**:
  - Número máximo de categorías: 10 ítems.
  - Comportamiento con exceso de categorías: Mostrar advertencia o agrupar el resto de categorias en otros.
- **Opciones de personalización**:
  - Colores: Paletas Personalizables por serie (ej. azul, verde).
  - Etiquetas: Mostrar valores encima de las barras y nombres de ítems en el eje X.
  - Formato de valores: Moneda (USD), enteros, decimales.
  - Ordenamiento: Por diferencia entre series (descendente) o alfabético.
  - Escalas: Lineal en eje Y.

## 5. Interactividad
- **Funcionalidades interactivas**:
  - Filtros: Seleccionar ítems específicos (top o bottom).
  - Tooltips: Mostrar valores exactos de Budget Spent y Budget Planned al pasar el cursor.
  - Zoom o desplazamiento: No aplica.
- **Eventos soportados**: Clic en barra para abrir detalle del ítem, exportar datos como CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento puede disminuir con más de 10 ítems; no soporta datos en tiempo real.
- **Casos no recomendados**: No usar para análisis de tendencias temporales (usar gráfico de líneas).

## 7. Ejemplo Práctico
- **Descripción**: Comparar el presupuesto gastado y planificado para los cinco proyectos con mayor desviación.
- **Datos de entrada**:
  ```
  | Ítem       | Budget Spent | Budget Planned |
  |------------|--------------|----------------|
  | Project 1  | $1000        | $800           |
  | Project 2  | $800         | $900           |
  | Project 3  | $500         | $600           |
  | Project 4  | $250         | $300           |
  | Project 5  | $0           | $250           |
  ```
- **Resultado visual**: 
  - Gráfico de barras verticales: Project 1 (azul $1000, verde $800), Project 2 (azul $800, verde $900), etc.
  - Etiquetas: Valores encima de cada barra (ej. $1000, $800).
  - Imagen: [Placeholder para imagen de gráfico de barras verticales con dos series].
- **Configuración aplicada**: Colores azul y verde, formato moneda (USD), orden por diferencia descendente.

## 8. Requerimientos Técnicos
- **Formato de salida**: Canvas.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo (móvil, desktop).

## 9. Notas Adicionales
- Considerar integración futura con alertas para desviaciones significativas.
- Optimizar para dashboards con múltiples widgets.