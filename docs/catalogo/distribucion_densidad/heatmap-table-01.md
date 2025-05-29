# Tabla con Heatmap

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Tabla que muestra datos numéricos con un gradiente de color (heatmap) para resaltar valores altos y bajos.
- **Identificador único**: `HEATMAP_TABLE_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Visualizar la estructura de deuda o cualquier métrica con énfasis visual en los valores mediante colores.
- **Casos de uso**:
  - Mostrar la estructura de deuda por cliente y rango de días.
  - Analizar la distribución de gastos por categoría con intensidad.
  - Representar el envejecimiento de cuentas por cobrar.
- **Tipos de análisis soportados**: Descriptivo, comparativo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
  - Mínimo: 1 variable categórica (etiqueta de fila), 1 variable categórica (etiqueta de columna), 1 variable numérica (valor).
  - Máximo: 5 variables categóricas (filas), 5 variables categóricas (columnas), 1 variable numérica (valores).
  - Tipos de datos: Categórico (etiquetas), numérico (valores).
  - **Estructura de datos** (grilla):

    | Cliente        | 0-30 DAYS  | 30-60 DAYS | >60 DAYS |
    |----------------|------------|------------|----------|
    | Customer 40546 | -          | $318,294   | $318,294 |
    | Customer 40547 | $67,634    | $302,294   | $12,294  |
    | Customer 40548 | $175,634   | -          | -        |
    | Customer 40549 | $33,567    | -          | $5,460   |
    | Customer 40550 | $10,234    | $10,234    | $10,234  |
    | Customer 40551 | $7,634     | $42,294    | $22,294  |
    | Customer 40552 | $55,567    | $9         | -        |
    | Customer 40553 | $13,567    | -          | -        |

- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: Hasta 25 celdas; recomendado 15.

## 4. Configuración Visual
- **Estructura del gráfico**:
  - Tabla con celdas coloreadas según un gradiente (ej. azul de bajo a alto).
  - Dimensiones: Mínimo 300x200 px, adaptable.
- **Categorías/Series**:
  - Máximo 5 filas x 5 columnas.
  - Exceso: Mostrar advertencia o paginación.
- **Opciones de personalización**:
  - Colores: Gradiente personalizable (ej. azul claro a azul oscuro). El widget debe detectar automáticamente los valores máximo y mínimo de los datos para asignar el gradiente de color correctamente, donde el valor mínimo se asocia con el color más claro y el valor máximo con el color más oscuro del gradiente elegido.
  - Etiquetas: Mostrar nombres de filas/columnas y valores.
  - Formato de valores: Moneda (USD), enteros, decimales.
  - Ordenamiento: Por valor (ascendente/descendente) o alfabético.
  - Escalas: Gradiente basado en el rango de valores (mínimo a máximo).

## 5. Interactividad
- **Funcionalidades interactivas**:
  - Filtros: Seleccionar rangos o clientes.
  - Tooltips: Mostrar valor exacto al pasar el cursor.
  - Zoom: No aplica.
- **Eventos soportados**: Clic en celda para detalle, exportar como CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 25 celdas.
- **Casos no recomendados**: No usar para tendencias temporales (usar gráfico de líneas).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar la estructura de deuda por cliente y rango de días.
- **Datos de entrada**:
  ```
  | Cliente        | 0-30 DAYS  | 30-60 DAYS | >60 DAYS |
  |----------------|------------|------------|----------|
  | Customer 40546 | -          | $318,294   | $318,294 |
  | Customer 40547 | $67,634    | $302,294   | $12,294  |
  | Customer 40548 | $175,634   | -          | -        |
  | Customer 40549 | $33,567    | -          | $5,460   |
  | Customer 40550 | $10,234    | $10,234    | $10,234  |
  | Customer 40551 | $7,634     | $42,294    | $22,294  |
  | Customer 40552 | $55,567    | $9         | -        |
  | Customer 40553 | $13,567    | -          | -        |
  ```
- **Resultado visual**: Tabla con gradiente azul (bajo: claro, alto: oscuro), valores en USD, celdas vacías como "-". El valor máximo ($318,294) se muestra en azul oscuro, y el valor mínimo ($5,460) en azul claro.
- **Configuración aplicada**: Gradiente azul, formato moneda (USD), orden alfabético.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 370px; position: relative;">
  <iframe src="../../../assets/widgets_html/densidad/heatmap_table_01_interactive.html" 
          style="width: 100%; height: 370px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo de Heatmap">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 370px; /* Ajusta según la altura típica de tus widgets */
}
</style>

## 8. Requerimientos Técnicos
- **Dependencias**: HTML/CSS, D3.js.
- **Formato de salida**: HTML.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Asegurar que el gradiente sea legible y proporcional a los valores.
- Permitir ajuste de intensidad del gradiente.