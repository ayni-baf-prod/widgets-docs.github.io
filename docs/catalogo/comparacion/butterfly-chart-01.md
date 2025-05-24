# Gráfico de Mariposa

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico que compara dos series de datos opuestas de manera simétrica alrededor de un eje central, utilizando barras para visualizar diferencias entre dos indicadores en distintos contextos, ya sean variables categóricas o de temporalidad.
- **Identificador único**: `BUTTERFLY_CHART_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Comparar visualmente dos conjuntos de datos opuestos para identificar diferencias por categoría o período.
- **Casos de uso**:
    - Comparar ingresos y gastos por departamento.
    - Comparar impuestos por crédito e impuestos por pagar por mes.
    - Analizar ganancias y pérdidas por producto o región.
- **Tipos de análisis soportados**: Comparativo, descriptivo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable categórica o temporal (eje X), 2 variables numéricas (series opuestas).
    - Máximo: 1 variable categórica o temporal, 2 variables numéricas.
    - Tipos de datos: Categórico o temporal (categorías/meses), numérico (valores).
  - **Estructura de datos** (grilla):
    ```
    | Región        | Clientes Activos | Clientes Perdidos |
    |---------------|------------------|-------------------|
    | Central       | 1651             | 685               |
    | Mid-Atlantic  | 1488             | 576               |
    | Northeast     | 1202             | 442               |
    | Northwest     | 229              | 90                |
    | South         | 559              | 335               |
    | Southeast     | 405              | 158               |
    ```
- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: Hasta 12 categorías (ej. 12 meses); recomendado 6.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Barras opuestas simétricas alrededor de un eje central (0), con una serie extendiéndose a la derecha y la otra a la izquierda.
    - Dimensiones: Mínimo 600x400 px, adaptable.
- **Categorías/Series**:
    - Máximo 12 categorías.
    - Exceso: Mostrar advertencia o truncar.
- **Opciones de personalización**:
    - Colores: Dos colores personalizables (ej. rojo para una serie, verde para la otra).
    - Etiquetas: Mostrar/ocultar valores en las barras.
    - Formato de valores: Enteros, decimales.
    - Ordenamiento: Por valor (descendente), alfabético o cronológico.
    - Escalas: Simétrica alrededor de 0.

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar categorías específicas.
    - Tooltips: Mostrar valores exactos al pasar el cursor.
    - Zoom: No aplica.
- **Eventos soportados**: Clic en barra para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 12 categorías.
- **Casos no recomendados**: No usar para tendencias temporales continuas (usar gráfico de líneas).

## 7. Ejemplo Práctico
- **Descripción**: Comparar clientes activos y perdidos por región.
- **Datos de entrada**:
  ```
  | Región        | Clientes Activos | Clientes Perdidos |
  |---------------|------------------|-------------------|
  | Central       | 1651             | 685               |
  | Mid-Atlantic  | 1488             | 576               |
  | Northeast     | 1202             | 442               |
  | Northwest     | 229              | 90                |
  | South         | 559              | 335               |
  | Southeast     | 405              | 158               |
  ```
- **Resultado visual**: Gráfico de mariposa con barras rojas (activos) a la derecha y verdes (perdidos) a la izquierda, valores enteros visibles. 
- **Configuración aplicada**: Colores rojo/verde, etiquetas visibles, orden alfabético.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 500px; position: relative;">
  <iframe src="../../../assets/widgets_html/BUTTERFLY_CHART_01/butterfly_chart_interactive.html" 
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
- **Formato de salida**: SVG.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Asegurar que las barras sean simétricas y legibles.
- Permitir ajuste manual del ancho de barras.