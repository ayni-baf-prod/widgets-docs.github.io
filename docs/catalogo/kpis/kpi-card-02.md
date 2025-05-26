# Tarjeta de KPI con Tendencia

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Widget que muestra un indicador clave de rendimiento (KPI) con un valor principal, variación comparativa y una línea de tendencia basada en datos históricos.
- **Identificador único**: `KPI_CARD_02`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Presentar un indicador financiero o operativo con su evolución visual a través de una línea de tendencia.
- **Casos de uso**:
    - Mostrar ingresos totales con tendencia mensual.
    - Visualizar gastos con comparación al presupuesto y evolución histórica.
    - Indicar impuestos recaudados con tendencia trimestral.
- **Tipos de análisis soportados**: Descriptivo, temporal.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable temporal (fecha), 1 variable numérica (valor histórico), 1 variable numérica (variación porcentual).
    - Máximo: 1 variable temporal (hasta 12 puntos), 1 variable numérica (valor histórico), 1 variable numérica (variación porcentual).
    - Tipos de datos: Temporal (fechas), numérico (valores, variación).
  - **Estructura de datos** (grilla):

    | Indicador       | Fecha       | Valor Histórico (USD) | Variación % |
    |-----------------|-------------|-----------------------|-------------|
    | Revenue         | Mar 2025    | 95M                   | 5.3%        |
    | Revenue         | Apr 2025    | 96M                   | 1.1%        |
    | Revenue         | May 2025    | 98.67M                | 2.8%        |

    - Nota: La variación porcentual a mostrar debe de estar en la estructura de datos que consumirá el widget y representa el cambio respecto al último periodo anterior.
- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: Hasta 12 puntos de tendencia.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Tarjeta rectangular con título, el último valor de la temporalidad como valor del indicador principal, variación porcentual y una pequeña línea de tendencia en la parte inferior basada en los datos históricos.
    - Dimensiones: Mínimo 200x150 px, adaptable.
- **Categorías/Series**:
    - Máximo 1 valor por tarjeta, 1 línea de tendencia.
   - Exceso: Mostrar advertencia o truncar tendencia a 12 puntos.
- **Opciones de personalización**:
    - Colores: Fondo, texto y línea de tendencia personalizables (ej. fondo blanco, texto negro, línea azul). Opciones para definir el color de la línea y su fondo (area debajo de la misma)
    - Etiquetas: Mostrar título, valor principal (último valor histórico), variación porcentual y leyenda opcional para tendencia.
    - Formato de valores: Moneda (USD), %, enteros, decimales.
    - Umbral/Símbolo de tendencia: Opción para mostrar flecha hacia arriba (incremental) o abajo (decremental), con colores personalizables.
    - Posición del indicador secundario (variación): Seleccionable entre parte inferior o derecha.
    - Ordenamiento: No aplica.
    - Escalas: No aplica para tendencia (proporcional al valor principal).

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: No aplica, pero permite que otros filtros lo afecten.
    - Tooltips: Mostrar detalle del valor y puntos de tendencia al pasar el cursor.
    - Zoom: No aplica.
- **Eventos soportados**: No aplica.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 12 puntos de tendencia.
- **Casos no recomendados**: No usar para múltiples indicadores (usar gráfico).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar ingresos con variación y tendencia.
- **Datos de entrada**:

  ```
  | Indicador | Fecha  | Valor Histórico (USD) | Variación % |
  |-----------|--------|-----------------------|-------------|
  | Revenue   | Jan-25 | 910,082               | 0.0000      |
  | Revenue   | Feb-25 | 882,187               | -0.0307     |
  | Revenue   | Mar-25 | 815,091               | -0.0761     |
  | Revenue   | Apr-25 | 968,083               | 0.1877      |
  | Revenue   | May-25 | 954,673               | -0.0139     |
  | Revenue   | Jun-25 | 890,519               | -0.0672     |
  | Revenue   | Jul-25 | 893,508               | 0.0034      |
  | Revenue   | Aug-25 | 918,822               | 0.0283      |
  | Revenue   | Sep-25 | 817,864               | -0.1099     |
  | Revenue   | Oct-25 | 938,681               | 0.1477      |
  | Revenue   | Nov-25 | 886,332               | -0.0558     |
  | Revenue   | Dec-25 | 919,019               | 0.0369      |
  ```

- **Resultado visual**: Tarjeta con título "Revenue", valor principal "919K" (último valor de Dec-2025), variación "3.7%" en la parte inferior del indicador principal, flecha verde hacia arriba, línea de tendencia azul en la parte inferior, fondo blanco, texto negro.

- **Configuración aplicada**: Formato moneda (USD), fondo blanco, texto negro, línea azul, flecha verde.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 270px; position: relative;">
  <iframe src="../../../assets/widgets_html/KPIS/kpi_card_02_interactive.html" 
          style="width: 100%; height: 270px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo del Filtro">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 270px; /* Ajusta según la altura típica de tus widgets */
}
</style>

## 8. Requerimientos Técnicos
- **Formato de salida**: HTML.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Asegurar que la línea de tendencia sea legible y proporcional al espacio disponible.
- Permitir ajuste de grosor de la línea de tendencia.