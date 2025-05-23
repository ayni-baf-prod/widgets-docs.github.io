# Grilla de Indicadores

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Grilla que muestra indicadores financieros con valores, variaciones porcentuales y umbrales visuales (ej. flechas de aumento/disminución).
- **Identificador único**: `INDICATOR_GRID_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Resumir indicadores clave con variaciones y umbrales para análisis financiero.
- **Casos de uso**:
    - Mostrar un estado de resultados con métricas como ingresos, costos, EBIT y utilidad neta.
    - Comparar desempeño financiero con períodos anteriores.
- **Tipos de análisis soportados**: Descriptivo, comparativo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable categórica (nombre del indicador), 1 variable numérica (valor), 1 variable numérica (variación %).
    - Máximo: 10 indicadores con sus valores y variaciones.
    - Tipos de datos: Categórico (indicador), numérico (valor, variación).
  - **Estructura de datos** (grilla):
    ```
    | Indicador         | Valor (USD) | Variación % |
    |------------------|-------------|-------------|
    | Revenue          | 98,670,000  | 9.5%        |
    | Cost of Goods    | 44,400,000  | 4.7%        |
    | Gross Profit     | 54,260,000  | 0.8%        |
    ```
- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: Hasta 20 indicadores; recomendado 10 para legibilidad.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Grilla con columnas: Indicador, Valor, Variación % (con flecha de aumento/disminución).
    - Dimensiones: Mínimo 300x400 px, adaptable.
- **Categorías/Series**:
    - Máximo 10 indicadores (filas).
    - Exceso: Mostrar advertencia o paginación.
- **Opciones de personalización**:
    - Colores: Flechas verdes (aumento), rojas (disminución), texto personalizable.
    - Etiquetas: Mostrar/ocultar variaciones.
    - Formato de valores: Moneda (USD), %, decimales.
    - Presentación de filas: Opción para resaltar filas como total (ej. negrita, fondo diferente), similar a "Gross Profit".
    - Ordenamiento: Alfabético o por valor (ascendente/descendente).
    - Escalas: No aplica.

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar indicadores específicos.
    - Tooltips: Mostrar detalle del indicador al pasar el cursor.
    - Zoom: No aplica.
- **Eventos soportados**: Clic en fila para detalle, exportar como CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 20 indicadores.
- **Casos no recomendados**: No usar para datos temporales largos (usar gráfico de líneas).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar estado de resultados con indicadores clave.
- **Datos de entrada**:
  ```
  | Indicador         | Valor (USD) | Variación % |
  |------------------|-------------|-------------|
  | Revenue          | 98,670,000  | 9.5%        |
  | Cost of Goods    | 44,400,000  | 4.7%        |
  | Gross Profit     | 54,260,000  | 0.8%        |
  ```
- **Resultado visual**: Grilla con 3 filas, columna de indicadores, valores en USD, variación % con flechas (verde para aumento), "Gross Profit" en negrita como total. Imagen: [Placeholder para imagen de grilla con "Gross Profit" en negrita].
- **Configuración aplicada**: Formato moneda (USD), flechas verdes/rojas, "Gross Profit" en negrita.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 350px; position: relative;">
  <iframe src="../../../assets/widgets_html/INDICATOR_GRID_01/indicator_grid_01_interactive.html" 
          style="width: 100%; height: 350px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo de la grilla">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 350px; /* Ajusta según la altura típica de tus widgets */
}
</style>

## 8. Requerimientos Técnicos
- **Formato de salida**: HTML/CSS.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Considerar resaltado condicional para umbrales (ej. rojo si variación < 0).