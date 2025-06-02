# Gráfico de Líneas

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico que muestra la evolución de múltiples métricas numéricas a lo largo del tiempo mediante líneas.
- **Identificador único**: `LINE_CHART_02`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Visualizar tendencias temporales de métricas clave.
- **Casos de uso**:
  - Mostrar la evolución de ingresos netos, utilidad operativa y utilidad neta por trimestre.
  - Analizar tendencias de ventas o costos a lo largo del tiempo.
- **Tipos de análisis soportados**: Descriptivo, temporal.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable temporal (eje X), 1 variable numérica (eje Y).
  - Máximo: 1 variable temporal, 5 variables numéricas (series).
  - Tipos de datos: Temporal (fechas), numérico (valores).
  - **Estructura de datos** (grilla):
    ```
    | Fecha     | Ingresos Netos (USD) | Utilidad Operativa (USD) | Utilidad Neta (USD) |
    |-----------|----------------------|--------------------------|---------------------|
    | Q1 2022   | 14,800M              | 8,500M                   | 6,200M              |
    | Q2 2022   | 15,500M              | 9,400M                   | 6,800M              |
    | Q3 2022   | 16,200M              | 9,800M                   | 7,100M              |
    | Q4 2022   | 16,900M              | 10,200M                  | 7,400M              |
    | Q1 2023   | 17,200M              | 6,500M                   | 3,200M              |
    | Q2 2023   | 16,500M              | 7,400M                   | 4,800M              |
    | Q3 2023   | 14,200M              | 8,800M                   | 7,100M              |
    | Q4 2023   | 16,100M              | 11,200M                  | 8,400M              |
    ```
- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: Hasta 100 puntos temporales; recomendado 12 (mensual) o 4 (trimestral).

## 4. Configuración Visual
- **Estructura del gráfico**:
  - Líneas conectando puntos temporales, con ejes X (tiempo) y Y (valores).
  - Dimensiones: Mínimo 600x400 px, adaptable.
- **Categorías/Series**:
  - Máximo 5 series (líneas).
  - Exceso: Mostrar advertencia o truncar.
- **Opciones de personalización**:
  - Colores: Líneas con paletas personalizables (ej. azul, verde, rojo por serie).
  - Etiquetas: Mostrar/ocultar valores en puntos.
  - Formato de valores: Moneda (USD), decimales.
  - Ordenamiento: Cronológico en eje X.
  - Escalas: Lineal o logarítmica en eje Y.

## 5. Interactividad
- **Funcionalidades interactivas**:
  - Filtros: Seleccionar rango temporal o series.
  - Tooltips: Mostrar valor exacto al pasar el cursor.
  - Zoom: En eje X para rangos temporales.
- **Eventos soportados**: Clic en punto para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 100 puntos o 5 series.
- **Casos no recomendados**: No usar para datos categóricos (usar gráfico de barras).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar la evolución de métricas financieras en 2022.
- **Datos de entrada**:
  ```
  | Fecha     | Ingresos Netos (USD) | Utilidad Operativa (USD) | Utilidad Neta (USD) |
  |-----------|----------------------|--------------------------|---------------------|
  | Q1 2022   | 14,800M              | 8,500M                   | 6,200M              |
  | Q2 2022   | 15,500M              | 9,400M                   | 6,800M              |
  | Q3 2022   | 16,200M              | 9,800M                   | 7,100M              |
  | Q4 2022   | 16,900M              | 10,200M                  | 7,400M              |
  | Q1 2023   | 17,200M              | 6,500M                   | 3,200M              |
  | Q2 2023   | 16,500M              | 7,400M                   | 4,800M              |
  | Q3 2023   | 14,200M              | 8,800M                   | 7,100M              |
  | Q4 2023   | 16,100M              | 11,200M                  | 8,400M              |
  ```
- **Resultado visual**: Gráfico con 3 líneas (azul para Ingresos Netos, verde para Utilidad Operativa, rojo para Utilidad Neta), eje X trimestral, valores en USD. Imagen: [Placeholder para imagen de gráfico de líneas].
- **Configuración aplicada**: Colores azul/verde/rojo, formato moneda (USD), etiquetas visibles.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 480px; position: relative;">
  <iframe src="../../../assets/widgets_html/comparacion/line_chart_01_interactive.html" 
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
- Asegurar que el eje X sea legible con muchos puntos temporales.
- Permitir personalización de grosor de líneas.