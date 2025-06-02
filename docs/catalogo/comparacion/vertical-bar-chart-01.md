# Gráfico de Barras

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de barras para comparar valores numéricos entre categorías.
- **Identificador único**: `VERTICAL_BAR_CHART_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Comparar valores numéricos entre diferentes categorías o grupos.
- **Casos de uso**:
    - Comparar ventas por región en un trimestre.
    - Mostrar número de clientes por segmento de mercado.
- **Tipos de análisis soportados**: Descriptivo, comparativo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable numérica (valor), 1 variable categórica (categoría).
    - Máximo: 1 variable numérica, 1 variable categórica, 1 variable temporal (opcional para agrupar).
    - Tipos de datos: Numérico (valor), categórico (categoría), temporal (opcional).
  - **Estructura de datos** (grilla):
    ```
  | Región    | Ventas (USD) |
  |-----------|--------------|
  | Norte     | 600,000      |
  | Sur       | 900,000      |
  | Este      | 550,000      |
  | Oeste     | 650,000      |
  | Centro    | 950,000      |
    ```
- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: Hasta 10,000 registros; recomendado hasta 50 categorías para legibilidad.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Barras verticales u horizontales, eje X (categorías), eje Y (valores).
    - Dimensiones: Mínimo 400x300 px, adaptable a pantalla.
- **Categorías/Series**:
    - Máximo 12 categorías (ej. 12 regiones).
    - Exceso de categorías: Mostrar advertencia o agrupar en "Otros".
- **Opciones de personalización**:
    - Colores: Paleta personalizable (máximo 12 colores distintos).
    - Etiquetas: Mostrar/ocultar valores en barras.
    - Formato de valores: %, decimales (0-2), moneda (USD, EUR, etc.).
    - Ordenamiento: Ascendente/descendente por valor o alfabéticamente por categoría.
    - Escalas: Lineal (predeterminado), logarítmica.
    - Orientación: Vertical (predeterminado), horizontal.

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar categorías específicas.
    - Drill-down: De región a ciudad (si hay datos jerárquicos).
    - Tooltips: Mostrar valor exacto y categoría al pasar el cursor.
    - Zoom: No aplicable.
- **Eventos soportados**: Clic en barra para abrir detalle, exportar como CSV/PNG.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 20 categorías.
- **Casos no recomendados**: No usar para tendencias temporales largas (usar gráfico de líneas).

## 7. Ejemplo Práctico
- **Descripción**: Comparar ventas por región en Q1 2025.
- **Datos de entrada**:
  ```
  | Región    | Ventas (USD) |
  |-----------|--------------|
  | Norte     | 600,000      |
  | Sur       | 900,000      |
  | Este      | 550,000      |
  | Oeste     | 650,000      |
  | Centro    | 950,000      |
  ```
- **Resultado visual**: Gráfico de barras verticales con 5 barras (una por región), colores distintos por barra, etiquetas de valores en USD, ordenado descendentemente por ventas. Eje Y en formato moneda, eje X con nombres de regiones. Imagen: [Placeholder para imagen de gráfico de barras con 4 barras de colores, etiquetas en USD].
- **Configuración aplicada**: Formato moneda (USD), etiquetas visibles, orden descendente, paleta de colores azules.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 480px; position: relative;">
  <iframe src="../../../assets/widgets_html/comparacion/vertical_bar_chart_01_interactive.html" 
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
- **Formato de salida**: SVG para escalabilidad.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo para móvil y desktop.

## 9. Notas Adicionales
- Considerar optimización para grandes datasets mediante paginación o muestreo.
- Posible integración futura con drill-down dinámico desde el datawarehouse.