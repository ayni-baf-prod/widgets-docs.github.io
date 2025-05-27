# Tacómetro de Progreso

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Widget de tipo tacómetro que mide el progreso de un indicador entre un valor inicial y un valor final, con variaciones que pueden representarse en días, horas o porcentajes.
- **Identificador único**: `GAUGE_CHART_02`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Visualizar el progreso de una métrica en relación con un rango definido (inicio y fin), indicando su estado actual.
- **Casos de uso**:
    - Mostrar los días promedio de cuentas por cobrar pendientes.
    - Indicar el tiempo de retraso en horas para entregas.
    - Representar el porcentaje de cumplimiento de un objetivo.
- **Tipos de análisis soportados**: Descriptivo, de progreso.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable numérica (valor actual), 1 variable numérica (valor inicial), 1 variable numérica (valor final).
    - Máximo: 1 variable numérica (valor actual), 1 variable numérica (valor inicial), 1 variable numérica (valor final), 1 variable categórica (etiqueta).
    - Tipos de datos: Numérico (valores), categórico (etiqueta).
  - **Estructura de datos** (grilla):

    | Indicador                   | Valor Actual | Valor Inicial | Valor Final | Etiqueta |
    |-----------------------------|--------------|---------------|-------------|----------|
    | Days Receivable Outstanding | 17           | 0             | 180         | Days     |

- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: 1 valor por widget.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Círculo o semicírculo con un segmento coloreado que indica el valor actual dentro de un rango definido (inicio a fin).
    - Dimensiones: Mínimo 150x150 px, adaptable.
- **Categorías/Series**:
    - Máximo 1 valor por widget.
    - Exceso: No aplica.
- **Opciones de personalización**:
    - Colores: Segmento y fondo personalizables (ej. azul para progreso, gris para fondo).
    - Etiquetas: Mostrar valor actual y etiqueta opcional (ej. "17 days").
    - Formato de valores: Enteros (días, horas), porcentajes.
    - Ordenamiento: No aplica.
    - Escalas: Rango configurable (ej. 0-180 días, 0-100%, 0-24 horas).

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: No aplica, pero permite que otros filtros lo afecten.
    - Tooltips: Mostrar detalle del valor al pasar el cursor.
    - Zoom: No aplica.
- **Eventos soportados**: Clic para detalle, exportar como PNG.

## 6. Limitaciones
- **Restricciones técnicas**: No aplica.
- **Casos no recomendados**: No usar para múltiples indicadores (usar gráfico de barras).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar los días promedio de cuentas por cobrar pendientes.
- **Datos de entrada**:
  ```
  | Indicador                   | Valor Actual | Valor Inicial | Valor Final | Etiqueta |
  |-----------------------------|--------------|---------------|-------------|----------|
  | Days Receivable Outstanding | 17           | 0             | 180         | Days     |
  ```
- **Resultado visual**: Semicírculo con segmento azul indicando 17 días dentro de un rango de 0-180 días, fondo gris, texto "17 days" en el centro. 
- **Configuración aplicada**: Color azul para segmento, fondo gris, etiquetas visibles.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 380px; position: relative;">
  <iframe src="../../../assets/widgets_html/progreso/gauge_chart_02_interactive.html" 
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
- **Dependencias**: HTML/CSS, SVG.
- **Formato de salida**: SVG.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Asegurar que el segmento sea legible y proporcional al rango.
- Permitir ajuste de grosor del segmento.