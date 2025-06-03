# Gráfico de Dona con Indicador Central

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de dona que muestra la distribución de un valor total en dos categorías y su variación porcentual respecto a un período anterior en el centro.
- **Identificador único**: `DONUT_CHART_02`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Visualizar la distribución en categorías de con un indicador clave (total y variación temporal) para evaluar tendencias y composiciones.
- **Casos de uso**: 
  - Mostrar la distribución de empleados por género con headcount total en Recursos Humanos.
  - Analizar la composición de ingresos por fuente con total y variación en finanzas.
  - Evaluar el uso de recursos por tipo con total y cambio en operaciones.
  - Comparar ventas por canal con total y variación en comercial.
  - Monitorear tareas por estado con total y cambio en proyectos.
- **Tipos de análisis soportados**: Distributivo, comparativo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
  - Número mínimo y máximo de variables: 1 variable categórica (categorías), 2 variable numérica (valores por categoría), 1 variable numérica (total), 1 variable numérica (variación porcentual).
  - Tipos de datos soportados: Categórico (categorías), numérico (valores, total, variación).
  - Estructura de datos: Ejemplo en formato de grilla:

    | Categoría   |  Total  | M (Masculino)  | F (Femenino) | Variación % |
    |-------------|---------|----------------|--------------|-------------|
    | Headcount   | 250     | 150            | 100          | -2%         |

- **Fuente de datos**: Tablas SQL desde un datawarehouse (ej. tabla de métricas por categoría y totales).
- **Volumen de datos**: Hasta 2 variable numéricas (valores por categoria).

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Dona que representa la distribución (hasta 2) de un indicador principal, con un valor total y variación porcentual en el centro.
    - La variación también se representa con una flecha (triángulo), hacia arriba si es positiva y hacia abajo si es negativa. el color debe ser configurable.
  - Dimensiones recomendadas: 300x300 px, adaptable.
- **Categorías/Series**:
  - Número máximo de categorías: 2.
  - Comportamiento con exceso de categorías: Agrupar en "Otros" con color neutro.
- **Opciones de personalización**:
  - Colores: Paletas Configurables por categoría (ej. azul, amarillo, ajustable).
  - Etiquetas: Mostrar Inicial de las distribuciones en leyenda, total y variación en el centro.
  - Formato de valores: Enteros (total), porcentajes (variación).
  - Tooltip: al pasar el mouse por cada distribución mostrar el nombre completo, el valor proporcional y su porcentaje.
  - Escalas: Proporcional al total en la dona.

## 5. Interactividad
- **Funcionalidades interactivas**:
  - Filtros: Seleccionar categorías específicas.
  - Tooltips: Mostrar valores por categoría al pasar el cursor.
  - Zoom: No aplica.
- **Eventos soportados**: Clic en sección para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 3 categorías.
- **Casos no recomendados**: No usar para tendencias temporales (usar gráfico de líneas).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar la distribución de empleados por género con headcount total.
- **Datos de entrada**:
  ```
    | Categoría   |  Total  | M (Masculino)  | F (Femenino) | Variación % |
    |-------------|---------|----------------|--------------|-------------|
    | Headcount   | 250     | 150            | 100          | -2%         |
  ```
- **Resultado visual**: 
  - Gráfico de dona: Masculino (azul, 60%), Femenino (amarillo, 40%).
  - Centro: "Headcount 250 -2% ▼".
- **Configuración aplicada**: Azul (Masculino), amarillo (Femenino); formato numérico y porcentual.

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 380px; position: relative;">
  <iframe src="../../../assets/widgets_html/progreso/donut_chart_02_interactive.html" 
          style="width: 100%; height: 380px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo del Filtro">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 380px; /* Ajusta según la altura típica de tus widgets */
}
</style>


## 8. Requerimientos Técnicos
- **Formato de salida**: Canvas.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo (móvil, desktop).

## 9. Notas Adicionales
- Asegurar legibilidad del texto central en diferentes fondos.
- Considerar opción de ocultar variación si no aplica.