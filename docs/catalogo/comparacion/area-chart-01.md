# Gráfico de Área

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico que muestra la evolución de una o más variables a lo largo del tiempo mediante un área sombreada bajo la línea.
- **Identificador único**: `AREA_CHART_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Visualizar la magnitud acumulada y la tendencia de una métrica financiera a lo largo del tiempo.
- **Casos de uso**:
    - Mostrar el flujo de efectivo libre acumulado por mes.
    - Representar la evolución de ingresos o gastos acumulados.
    - Analizar tendencias de efectivo disponible.
- **Tipos de análisis soportados**: Descriptivo, temporal.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
   - Mínimo: 1 variable temporal (eje X), 1 variable numérica (valor).
    - Máximo: 1 variable temporal, 2 variables numéricas (series).
    - Tipos de datos: Temporal (fechas), numérico (valores).
  - **Estructura de datos** (grilla):

    | Fecha       | Free Cash Flow (USD) |
    |-------------|----------------------|
    | Jan 2022    | 250K                 |
    | Feb 2022    | 300K                 |
    | Mar 2022    | 280K                 |
    | Apr 2022    | 320K                 |
    | May 2022    | 310K                 |
    | Jun 2022    | 340K                 |
    | Jul 2022    | 350K                 |
    | Aug 2022    | 360K                 |
    | Sep 2022    | 400K                 |

- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: Hasta 12 puntos temporales; recomendado 9.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Área sombreada bajo una línea que representa la evolución de la variable a lo largo del tiempo.
    - Dimensiones: Mínimo 400x300 px, adaptable.
- **Categorías/Series**:
    - Máximo 2 series (áreas).
    - Exceso: Mostrar advertencia o truncar.
- **Opciones de personalización**:
    - Colores: Área y línea personalizables (ej. área naranja, línea oscura).
    - Etiquetas: Mostrar valores en puntos clave o leyenda.
    - Formato de valores: Moneda (USD), enteros, decimales.
    - Ordenamiento: Cronológico en eje X.
    - Escalas: Lineal en eje Y.

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar rango temporal o series.
    - Tooltips: Mostrar valor exacto al pasar el cursor.
    - Zoom: En eje X para rangos temporales.
- **Eventos soportados**: Clic en área para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 12 puntos o 2 series.
- **Casos no recomendados**: No usar para comparaciones categóricas (usar gráfico de barras).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar la evolución del flujo de efectivo libre en 2022.
- **Datos de entrada**:
  ```
  | Fecha       | Free Cash Flow (USD) |
  |-------------|----------------------|
  | Jan 2022    | 250K                 |
  | Feb 2022    | 300K                 |
  | Mar 2022    | 280K                 |
  | Apr 2022    | 320K                 |
  | May 2022    | 310K                 |
  | Jun 2022    | 340K                 |
  | Jul 2022    | 350K                 |
  | Aug 2022    | 360K                 |
  | Sep 2022    | 400K                 |
  ```
- **Resultado visual**: Gráfico de área con área sombreada en naranja, línea oscura, eje X con meses, valores en USD. 
- **Configuración aplicada**: Color naranja para área, formato moneda (USD), etiquetas visibles.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 480px; position: relative;">
  <iframe src="../../../assets/widgets_html/comparacion/area_chart_01_interactive.html" 
          style="width: 100%; height: 480px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo de Gráfico Combinado">
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
- Asegurar que el área sea legible y no opaque los datos.
- Permitir ajuste de opacidad del área.