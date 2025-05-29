# Gráfico de Progreso Porcenctual de Barras Horizontal

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico que muestra el progreso Porcentual de categorías mediante barras horizontales, con longitudes proporcionales a los valores con respecto al 100%
- **Identificador único**: `HORIZONAL_BAR_CHART_02`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Comparar rendimiento de diferentes categorías de manera visual.
- **Casos de uso**:
    - Mostrar los principales clientes por cumplimiento de pagos.
    - Analizar el ranking de productos por contribución a los ingresos.
- **Tipos de análisis soportados**: Comparativo, descriptivo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable categórica (etiqueta), 1 variable numérica (valor porcentual).
    - Máximo: 1 variable categórica, 5 variables numéricas (valores).
    - Tipos de datos: Categórico (etiquetas), numérico (porcentajes).
  - **Estructura de datos** (grilla):

    | Cliente       | Porcentaje     |
    |---------------|----------------|
    | Customer 1    | 0.90           |
    | Customer 2    | 0.80           |
    | Customer 3    | 0.70           |
    | Customer 4    | 0.70           |
    | Customer 5    | 0.60           |
    | Customer 6    | 0.50           |
    | Customer 7    | 0.40           |
    | Customer 8    | 0.30           |
    | Customer 9    | 0.20           |
    | Customer 10   | 0.10           |

- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: Hasta 10 categorías; recomendado 5.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Barras horizontales con longitudes proporcionales a los valores, alineadas a la izquierda.
    - Dimensiones: Mínimo 300x200 px, adaptable.
- **Categorías/Series**:
    - Máximo 10 categorías.
    - Exceso: agrupar en otros.
- **Opciones de personalización**:
    - Colores: Barras personalizables (ej. azul para todas).
    - Etiquetas: Mostrar nombres de categorías y valores/porcentajes, ya sea por dentro o fuera de la barra.
    - Formato de valores: Porcentajes, moneda (USD), enteros.
    - Ordenamiento: Por valor (descendente) o alfabético.
    - Escalas: Lineal en eje X.
    - Debe de permitirse configurar la vista por defecto de 3 a más. si se configura la vista por 5 categorias y la data tiene 10 el widget debe de habilitar el scroll para deslizar y ver las otras categorias. 

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar categorías específicas.
    - Tooltips: Mostrar valor exacto al pasar el cursor.
    - Zoom: No aplica.
- **Eventos soportados**: Clic en barra para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 10 categorías.
- **Casos no recomendados**: No usar para tendencias temporales (usar gráfico de líneas).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar los cinco principales clientes por ventas.
- **Datos de entrada**:
  ```
    | Cliente       | Porcentaje     |
    |---------------|----------------|
    | Customer 1    | 0.90           |
    | Customer 2    | 0.80           |
    | Customer 3    | 0.70           |
    | Customer 4    | 0.70           |
    | Customer 5    | 0.60           |
    | Customer 6    | 0.50           |
    | Customer 7    | 0.40           |
    | Customer 8    | 0.30           |
    | Customer 9    | 0.20           |
    | Customer 10   | 0.10           |
  ```
- **Resultado visual**: Gráfico de barras horizontales con barras azules, etiquetas "Customer 1" a "Customer 10" con porcentajes (90%, 80%, 70%, 70%, 60%, 50%, 40%, 30%, 20%, 10%). 
- **Configuración aplicada**: Color azul para barras, formato porcentaje, orden descendente.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 400px; position: relative;">
  <iframe src="../../../assets/widgets_html/comparacion/horizontal_bar_chart_02_interactive.html" 
          style="width: 100%; height: 400px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo de Gráfico de barras horizontal">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 400px; /* Ajusta según la altura típica de tus widgets */
}
</style>

## 8. Requerimientos Técnicos
- **Formato de salida**: SVG.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Asegurar que las barras sean legibles y proporcionales.
- Permitir ajuste de ancho de barras.