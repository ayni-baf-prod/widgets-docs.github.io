# Mapa de Calor

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Mapa de calor que representa valores numéricos mediante colores para comparar desempeño entre categorías.
- **Identificador único**: `HEATMAP_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Visualizar la intensidad o cumplimiento de indicadores mediante colores para análisis comparativo.
- **Casos de uso**:
     - Mostrar ventas por unidad de negocio con niveles de cumplimiento (verde, naranja, rojo).
     - Comparar desempeño operativo por área.
- **Tipos de análisis soportados**: Descriptivo, comparativo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable categórica (categoría), 2 variables numéricas (valores).
    - Máximo: No aplica (solo 1 variable categórica y 2 numéricas).
    - Tipos de datos: Categórico (categoría), numérico (valores enteros o decimales).
 - **Estructura de datos** (grilla):
  ```
  | Categoría         | Valor (USD) | Cumplimiento |
  |-------------------|-------------|--------------|
  | Aynitech Factory  | 930,305     | 0.90         |
  | Network           | 826,097     | 0.70         |
  | ISocial Cube      | 653,309     | 0.50         |
  | Aynitech Group    | 254,441     | 0.40         |
  | TITI              | 229,132     | 0.20         |
  | TnT               | 170,431     | 0.30         |
  | ISC               | 56,920      | 0.80         |
  ```
- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: Hasta 100 celdas; recomendado 50.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Grilla de celdas coloreadas según rangos de valor.
    - Dimensiones: Mínimo 400x300 px, adaptable.
- **Categorías/Series**:
    - Máximo 10 categorías.
    - Exceso: Agrupar en otros con funciones para Sumar o promediar sus valores.
- **Opciones de personalización**:
    - Colores: Escala personalizable (ej. verde, naranja, rojo por rangos).
    - Etiquetas: Mostrar/ocultar valores en celdas.
    - Tootip: Mostrar valores al pasar el mouse.
    - Formato de valores: Permitir formatear los valores con %, cantidad de decimales, commas para miles, moneda, etc.
    - Ordenamiento: Alfabético por categoría o por montos.
    - Escalas: Rangos de color definidos (ej. 0%-34%, 35%-64%, 65%-100%).

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: No aplica, pero permite que otros filtros lo afecten.
    - Tooltips: Mostrar valor exacto al pasar el cursor.
    - Zoom: No aplica.
- **Eventos soportados**: Clic en celda para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 100 celdas.
- **Casos no recomendados**: No usar para datos temporales (usar gráfico de líneas).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar cumplimiento por categoría de negocio.
- **Datos de entrada**:
  ```
  | Categoría         | Valor (USD) | Cumplimiento |
  |-------------------|-------------|--------------|
  | Aynitech Factory  | 930,305     | 0.90         |
  | Network           | 826,097     | 0.70         |
  | ISocial Cube      | 653,309     | 0.50         |
  | Aynitech Group    | 254,441     | 0.40         |
  | TITI              | 229,132     | 0.20         |
  | TnT               | 170,431     | 0.30         |
  | ISC               | 56,920      | 0.80         |
  ```
- **Resultado visual**: Celdas coloreadas (rojo, amarillo, verde), cuyos tamaños van de acuerdo al valor y los colores al cumplimiento.
- **Configuración aplicada**: Escala de color (verde 65%-100%, naranja 35%-64%, rojo 0%-34%), formato moneda (USD).

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 370px; position: relative;">
  <iframe src="../../../assets/widgets_html/HEATMAP_01/heatmap_01_interactive.html" 
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
- **Formato de salida**: SVG.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Definir rangos de color dinámicamente según los datos.