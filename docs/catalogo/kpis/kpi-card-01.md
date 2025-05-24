# Tarjeta de KPI

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Widget que muestra un indicador clave de rendimiento (KPI) con un valor principal y una variación comparativa.
- **Identificador único**: `KPI_CARD_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Presentar un indicador financiero o operativo clave de manera clara y rápida.
- **Casos de uso**:
    - Mostrar ingresos netos totales con variación año tras año.
    - Visualizar el total de gastos con comparación al presupuesto.
    - Indicar impuestos por pagar con variación frente al objetivo.
- **Tipos de análisis soportados**: Descriptivo, comparativo.
- **Consideraciones para las variaciones**: La forma en que se interpretan las variaciones positivas o negativas respecto al presupuesto (budget) depende del contexto del indicador: si un valor positivo o negativo es beneficioso o perjudicial para el negocio. A continuación se explica ambos casos:

### 📈 Variación positiva vs. Budget

| Indicador                              | Interpretación (valor mayor al budget)         | Color     | Flecha     | Notas                                                      |
|----------------------------------------|------------------------------------------------|-----------|------------|------------------------------------------------------------|
| Ventas netas                | Más ventas de lo esperado                      | ✅ Verde   | 🔼 Arriba   | Buen desempeño comercial                                    |
| Costo de ventas     | Gastos superiores al presupuesto               | ❌ Rojo    | 🔼 Arriba   | Reduce rentabilidad                                         |

### 📉 Variación negativa vs. Budget

| Indicador                              | Interpretación (valor menor al budget)         | Color     | Flecha     | Notas                                                      |
|----------------------------------------|------------------------------------------------|-----------|------------|------------------------------------------------------------|
| Ventas netas                | Menos ingresos de lo esperado                  | ❌ Rojo    | 🔽 Abajo   | Impacto directo al negocio                                 |
| Costos de venta    | Gastos menores al presupuesto                  | ✅ Verde   | 🔽 Abajo   | Buen control de costos                                     |


## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable numérica (valor principal), 1 variable numérica (variación).
    - Máximo: 1 variable numérica (valor principal), 1 variable numérica (variación), 1 variable categórica (etiqueta).
  - Tipos de datos: Numérico (valores enteros, decimales o Porcentaje), categórico (etiqueta).
  - **Estructura de datos** (grilla):

    | Indicador       | Valor (USD) | Variación % |
    |-----------------|-------------|-------------|
    | Net Income      | 15.5B       | 7%          |
    | Total Expenses  | 5.8M        | -3%         |

- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: 1 valor por tarjeta.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Tarjeta rectangular con título, valor principal, variación y opcionalmente un símbolo de tendencia.
    - Dimensiones: Mínimo 200x100 px, adaptable.
- **Categorías/Series**:
    - Máximo 1 valor por tarjeta.
    - Exceso: No aplica.
- **Opciones de personalización**:
    - Colores: Fondo y texto personalizables (ej. fondo blanco, texto negro).
    - Etiquetas: Mostrar título y variación (ej. "Net Income", "+7% Y/Y").
    - Formato de valores: Moneda (USD), %, enteros, decimales.
    - Umbral/Símbolo de tendencia: Opción para mostrar flecha hacia arriba o abajo, con colores personalizables. Verde o rojo que dependerán del valor si es positivo y negativo y del contexto del indicador (si es beneficioso o perjudicial para el negocio).
    - Posición del indicador secundario (variación): Seleccionable entre parte inferior o derecha.
    - Ordenamiento: No aplica.
    - Escalas: No aplica.

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: No aplica, pero permite que otros filtros lo afecten.
    - Tooltips: Mostrar detalle del valor al pasar el cursor.
    - Zoom: No aplica.
- **Eventos soportados**: No aplica.

## 6. Limitaciones
- **Restricciones técnicas**: No aplica.
- **Casos no recomendados**: No usar para múltiples indicadores (usar tabla).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar ingresos netos con variación y tendencia.
- **Datos de entrada**:
  ```
  | Indicador       | Valor (USD) | Variación   |
  |-----------------|-------------|-------------|
  | Total Purchase  | 100000000   | 15000       |
  ```
- **Resultado visual**: Tarjeta con título "Net Income", valor "15.5B", variación "+7% Y/Y" a la derecha, flecha verde hacia arriba, fondo blanco, texto negro. 
- **Configuración aplicada**: Formato moneda (USD), fondo blanco, texto negro, flecha verde, variación a la derecha.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 200px; position: relative;">
  <iframe src="../../../assets/widgets_html/KPIS/kpi_card_01_interactive.html" 
          style="width: 100%; height: 200px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo del Filtro">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 200px; /* Ajusta según la altura típica de tus widgets */
}
</style>

## 8. Requerimientos Técnicos
- **Formato de salida**: HTML.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Asegurar que el texto y los símbolos sean legibles con el fondo seleccionado.