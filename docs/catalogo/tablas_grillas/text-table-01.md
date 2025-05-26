# Lista de Texto/Tabla

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Widget que presenta datos financieros o operativos en formato de lista o tabla simple, sin visualización gráfica avanzada.
- **Identificador único**: `TEXT_TABLE_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Mostrar valores numéricos clave de manera estructurada y legible.
- **Casos de uso**:
    - Resumir los componentes del estado de flujo de efectivo (ej. ingresos, gastos, inversiones).
    - Listar tendencias de efectivo en una tabla comparativa.
    - Presentar balances o subtotales financieros.
- **Tipos de análisis soportados**: Descriptivo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable categórica (etiqueta), 1 variable numérica (valor).
    - Máximo: 5 variables categóricas (etiquetas), 5 variables numéricas (valores).
    - Tipos de datos: Categórico (etiquetas), numérico (valores).
  - **Estructura de datos** (grilla):

    | Categoría              | Valor (USD) |
    |------------------------|-------------|
    | Net Income             | 1.64M       |
    | Deferred Taxes         | 1.61M       |
    | Depreciation           | 1.66M       |
    | Cash from Working Capital Items | -962.76K  |
    | Subtotal               | 3.93M       |

    - Nota: El subtotal puede provenir precalculado del datawarehouse o ser calculado automáticamente por el widget sumando los valores precedentes.
- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: Hasta 10 filas; las filas excedentes se agruparán en "Otros".

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Lista o tabla simple con etiquetas y valores alineados.
    - Dimensiones: Mínimo 300x200 px, adaptable.
- **Categorías/Series**:
    - Máximo 10 filas; las filas excedentes se agrupan en "Otros".
    - Exceso: Mostrar "Otros" con la suma de valores excedentes.
- **Opciones de personalización**:
    - Colores: Fondo y texto personalizables (ej. fondo blanco, texto negro).
    - Etiquetas: Mostrar/ocultar nombres de categorías.
    - Formato de valores: Moneda (USD), %, enteros, decimales.
    - Ordenamiento: Alfabético, numérico (ascendente/descendente).
    - Resaltado de filas: Opción para destacar filas como subtotales (ej. negrita, fondo diferente, bordes) con personalización del estilo.
    - Escalas: No aplica.

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar categorías específicas; el contenido puede verse afectado por otros widgets (filtros).
    - Tooltips: Mostrar detalle del valor al pasar el cursor.
    - Zoom: No aplica.
- **Eventos soportados**: Clic en fila para detalle, exportar como CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 10 filas.
- **Casos no recomendados**: No usar para visualizaciones comparativas complejas (usar gráficos).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar un resumen del estado de flujo de efectivo.
- **Datos de entrada**:
  ```
  | Categoría                       | Valor (USD) |
  |---------------------------------|-------------|
  | Net Income                      | 1.64M       |
  | Deferred Taxes                  | 1.61M       |
  | Depreciation                    | 1.66M       |
  | Cash from Working Capital Items | -962.76K    |
  | Subtotal                        | 3.93M       |
  ```
- **Resultado visual**: Tabla con columnas "Categoría" y "Valor (USD)", valores en formato moneda (USD), fila "Subtotal" en negrita con fondo gris claro, fondo blanco, texto negro. 
- **Configuración aplicada**: Formato moneda (USD), fondo blanco, texto negro, subtotal en negrita con fondo gris claro.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 430px; position: relative;">
  <iframe src="../../../assets/widgets_html/INDICATOR_GRID_01/text_table_01_interactive.html" 
          style="width: 100%; height: 430px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo de la grilla">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 430px; /* Ajusta según la altura típica de tus widgets */
}
</style>

## 8. Requerimientos Técnicos
- **Dependencias**: HTML/CSS puro.
- **Formato de salida**: HTML.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Asegurar que el texto sea legible con el fondo seleccionado.
- Permitir ajuste de ancho de columnas.