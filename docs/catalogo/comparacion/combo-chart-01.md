# Gráfico Combinado (Líneas y Barras)

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico combinado que muestra barras apiladas y líneas para comparar valores y tendencias simultáneamente, incluyendo valores con distintas unidades (ej. moneda y porcentaje).
- **Identificador único**: `COMBO_CHART_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Comparar distribuciones (barras) y tendencias (líneas) en un mismo contexto, como ingresos y porcentajes de utilidad, permitiendo visualizar valores con distintas unidades.
- **Casos de uso**:
    - Mostrar ingresos (barras) y porcentaje de EBIT (línea) a lo largo del tiempo.
    - Comparar costos (barras) y ganancias netas (línea) por año.
- **Tipos de análisis soportados**: Descriptivo, comparativo, tendencia.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 2 variables numéricas (ej. ingresos, porcentaje), 1 variable temporal.
    - Máximo: 3 variables numéricas (ej. ingresos, costos, porcentaje), 1 variable temporal.
    - Tipos de datos: Numérico (valores), temporal (eje X).
- **Estructura de datos** (grilla):
    ```
    | Año  | Revenue (USD) | Cost (USD) | EBIT % |
    |------|---------------|------------|--------|
    | 2018 | 200,000       | 150,000    | 25%    |
    | 2019 | 250,000       | 180,000    | 28%    |
    | 2020 | 300,000       | 220,000    | 27%    |
    ```
- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: Hasta 10,000 registros; recomendado hasta 10 años o 20 puntos temporales.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Barras apiladas (ej. ingresos y costos) y línea (ej. EBIT %).
    - Dimensiones: Mínimo 500x300 px, adaptable a pantalla.
- **Categorías/Series**:
    - Máximo 10 puntos temporales (ej. años o trimestres).
    - Exceso de categorías: Mostrar advertencia o paginación.
- **Opciones de personalización**:
    - Colores: Paleta personalizable (barras: azul/naranja, línea: amarillo).
    - Etiquetas: Mostrar/ocultar valores en barras y puntos de línea.
    - Formato de valores: Moneda (USD), % para líneas, decimales.
    - Formato de texto (valores y puntos temporales): Font personalizable (ej. Arial, Roboto), tamaño (8-16px), color (cualquier hexadecimal).
    - Ejes: Opción para ocultar líneas de ejes (tanto X como Y).
    - Ordenamiento: Cronológico por eje temporal.
    - Escalas: Eje Y izquierdo (valores en USD), eje Y derecho (%).

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar rango de años.
    - Tooltips: Mostrar valores exactos de barras y líneas al pasar el cursor.
    - Zoom: En eje temporal (ej. de años a trimestres).
- **Eventos soportados**: Clic en barra/línea para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 20 puntos temporales o 3 series.
- **Casos no recomendados**: No usar con datos geográficos o más de 3 variables numéricas (ilegibilidad).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar ingresos, costos y porcentaje de EBIT por año (2018-2023).
- **Datos de entrada**:
  ```
  | Año  | Revenue (USD) | Cost (USD) | EBIT % |
  |------|---------------|------------|--------|
  | 2018 | 200,000       | 150,000    | 25%    |
  | 2019 | 250,000       | 180,000    | 28%    |
  | 2020 | 300,000       | 220,000    | 27%    |
  | 2021 | 350,000       | 250,000    | 29%    |
  | 2022 | 400,000       | 300,000    | 25%    |
  | 2023 | 450,000       | 350,000    | 22%    |
  ```
- **Resultado visual**: Gráfico con barras apiladas (Revenue en azul, Cost en naranja) y línea amarilla para EBIT %, etiquetas en USD y %, eje X con años, sin líneas de ejes, texto en Poppins 12px negro.
- **Configuración aplicada**: Formato moneda ($), % para EBIT, etiquetas visibles, escala dual (USD/%), se muestran ejes, texto en Poppins 12px negro.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 500px; position: relative;">
  <iframe src="../../../assets/widgets_html/COMBO_CHART_01/combo_chart_interactive.html" 
          style="width: 100%; height: 500px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo de Gráfico Combinado">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 550px; /* Ajusta según la altura típica de tus widgets */
}
</style>


## 8. Requerimientos Técnicos
- **Formato de salida**: SVG para escalabilidad.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Optimizar con muestreo para datasets grandes.
- Posible integración con drill-down a trimestres desde el datawarehouse.