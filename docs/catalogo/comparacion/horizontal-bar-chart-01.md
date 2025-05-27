# Gráfico de Barras Horizontal

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico que muestra la comparación de categorías mediante barras horizontales, con longitudes proporcionales a los valores.
- **Identificador único**: `HORIZONAL_BAR_CHART_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Comparar la contribución o rendimiento de diferentes categorías de manera visual.
- **Casos de uso**:
    - Mostrar los principales clientes por ventas.
    - Representar la distribución de cuentas por cobrar por cliente.
    - Analizar el ranking de productos por ingresos.
- **Tipos de análisis soportados**: Comparativo, descriptivo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable categórica (etiqueta), 1 variable numérica (valor).
    - Máximo: 1 variable categórica, 5 variables numéricas (valores).
    - Tipos de datos: Categórico (etiquetas), numérico (porcentajes o valores).
  - **Estructura de datos** (grilla):

    | Cliente       | average days    |
    |---------------|-----------------|
    | Customer 1    | 178             |
    | Customer 2    | 150             |
    | Customer 3    | 141             |
    | Customer 4    | 120             |
    | Customer 5    | 115             |
    | Customer 6    | 110             |
    | Customer 7    | 100             |
    | Customer 8    | 80              |
    | Customer 9    | 70              |
    | Customer 10   | 50              |

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
    | Cliente       | average days    |
    |---------------|-----------------|
    | Customer 1    | 178             |
    | Customer 2    | 150             |
    | Customer 3    | 141             |
    | Customer 4    | 120             |
    | Customer 5    | 115             |
    | Customer 6    | 110             |
    | Customer 7    | 100             |
    | Customer 8    | 80              |
    | Customer 9    | 70              |
    | Customer 10   | 50              |
  ```
- **Resultado visual**: Gráfico de barras horizontales con barras azules, etiquetas "Customer 1" a "Customer 5" con porcentajes (20%, 17%, 15%, 8%, 5%). 
- **Configuración aplicada**: Color azul para barras, formato porcentaje, orden descendente.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 480px; position: relative;">
  <iframe src="../../../assets/widgets_html/comparacion/horizontal_bar_chart_01_interactive.html" 
          style="width: 100%; height: 480px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo de Gráfico de barras horizontal">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 480px; /* Ajusta según la altura típica de tus widgets */
}
</style>

## 8. Requerimientos Técnicos
- **Formato de salida**: SVG.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Asegurar que las barras sean legibles y proporcionales.
- Permitir ajuste de ancho de barras.