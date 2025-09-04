# Gráfico de Burbujas Multi-Indicador

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de burbujas interactivo que permite seleccionar dinámicamente qué indicadores visualizar en los ejes X e Y, manteniendo un tercer indicador fijo para el tamaño de las burbujas. Facilita análisis multivariable flexible y comparativo.
- **Identificador único**: `MULTI_INDICATOR_BUBBLE_CHART_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Proporcionar una visualización flexible que permita al usuario explorar diferentes combinaciones de indicadores para identificar correlaciones, patrones o excepciones, con capacidad de cambiar la perspectiva de análisis dinámicamente.
- **Casos de uso**:
    - **Comercial**: Analizar productos comparando diferentes métricas como market share vs profit margin, sales growth rate vs expenses, con volumen de ventas como tamaño fijo.
    - **Finanzas**: Evaluar portafolios de inversión alternando entre rentabilidad vs riesgo, ROI vs liquidez, con monto invertido como tamaño.
    - **Recursos Humanos**: Comparar empleados entre performance vs satisfacción, experiencia vs salario, con carga de trabajo como tamaño.
    - **Operaciones**: Analizar plantas entre producción vs costos, eficiencia vs calidad, con capacidad instalada como tamaño.
    - **Marketing**: Evaluar campañas entre reach vs engagement, CTR vs conversion rate, con presupuesto como tamaño.
- **Tipos de análisis soportados**: Descriptivo, comparativo, correlacional, exploratorio multivariable.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable categórica (elemento), 3 variables numéricas (2 para ejes + 1 para tamaño).
    - Máximo: 1 variable categórica (elemento), ilimitadas variables numéricas para indicadores.
    - Estructura flexible: Nombres de indicadores dinámicos según caso de uso.
    - Marcador de tamaño: Un indicador debe estar marcado como `is_size_indicator = true`.
- **Estructura de datos** (formato normalizado):

  | Elemento   | Indicador_Name       | Valor | is_size_indicator | Label_Indicador     |
  |------------|---------------------|-------|------------------|---------------------|
  | Producto A | Market_Share        | 25.5  | false            | Market Share (%)    |
  | Producto A | Profit_Margin       | 15.2  | false            | Profit Margin (%)   |
  | Producto A | Sales_Volume        | 1200  | true             | Sales Volume (Units)|
  | Producto A | Growth_Rate         | 8.3   | false            | Growth Rate (%)     |
  | Producto B | Market_Share        | 18.7  | false            | Market Share (%)    |
  | Producto B | Profit_Margin       | 22.1  | false            | Profit Margin (%)   |
  | Producto B | Sales_Volume        | 950   | true             | Sales Volume (Units)|
  | Producto B | Growth_Rate         | 12.5  | false            | Growth Rate (%)     |

- **Fuente de datos**: Tablas SQL desde datawarehouse con estructura normalizada de indicadores.
- **Volumen de datos**: Hasta 50 elementos; sin límite en número de indicadores (recomendado 3-10 para UX óptima).

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Panel principal: Gráfico de burbujas con ejes X,Y seleccionables.
    - Panel de control: Selectores de indicadores con radio buttons agrupados por eje.
    - Grid de referencia: Líneas cada 10% para orientación visual.
    - Dimensiones: Mínimo 600x400 px, completamente responsivo.
    - Layout: Controles a la derecha en desktop, abajo en móvil (<768px).
- **Categorías/Series**:
   - Máximo 50 elementos (agrupar excedentes en "OTROS" si es necesario).
   - Indicadores: Sin límite, agrupados en selectores X e Y.
- **Opciones de personalización**:
    - Colores: Paleta profesional configurable por elemento.
    - Tamaños de burbujas: Escala proporcional del indicador de tamaño (rango 5-25px radio).
    - Etiquetas: Configurables en tooltips y selectores.
    - Formato de valores: Automático según tipo (%, decimales, enteros).
    - Escalas: Dinámicas según indicadores seleccionados.
    - Posición de controles: Configurable (derecha, abajo, colapsable).

## 5. Interactividad
- **Funcionalidades interactivas**:
    - **Selectores de ejes**: Radio buttons agrupados para X e Y con validación cruzada.
    - **Preselección inteligente**: Primer y segundo indicador no-tamaño como defaults.
    - **Validación**: Deshabilitar indicador ya seleccionado en el otro eje.
    - **Tooltips dinámicos**: Mostrar valores de ejes activos + tamaño con labels claros.
    - **Efectos hover**: Resaltado suave de burbujas con información contextual.
    - **Redimensionamiento**: Auto-ajuste con debounce de 250ms.
- **Eventos soportados**: Cambio de ejes (recálculo automático), clic en elemento para detalle, exportar vista actual.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento óptimo hasta 50 elementos; más de 15 indicadores puede impactar UX de selección.
- **Casos no recomendados**: Datos temporales (usar LINE_CHART_01), menos de 3 indicadores totales.
- **Validaciones**: Exactamente un indicador debe estar marcado como `is_size_indicator = true`.

## 7. Ejemplo Práctico
- **Descripción**: Dashboard de análisis de productos con capacidad de alternar entre diferentes métricas de performance.
- **Datos de entrada**:
  ```
  | Elemento   | Indicador_Name       | Valor | is_size_indicator | Label_Indicador     |
  |------------|---------------------|-------|------------------|---------------------|
  | Producto A | Market_Share        | 25.5  | false            | Market Share (%)    |
  | Producto A | Profit_Margin       | 15.2  | false            | Profit Margin (%)   |
  | Producto A | Sales_Volume        | 1200  | true             | Sales Volume (Units)|
  | Producto A | Growth_Rate         | 8.3   | false            | Growth Rate (%)     |
  | Producto B | Market_Share        | 18.7  | false            | Market Share (%)    |
  | Producto B | Profit_Margin       | 22.1  | false            | Profit Margin (%)   |
  | Producto B | Sales_Volume        | 950   | true             | Sales Volume (Units)|
  | Producto B | Growth_Rate         | 12.5  | false            | Growth Rate (%)     |
  | Producto C | Market_Share        | 31.2  | false            | Market Share (%)    |
  | Producto C | Profit_Margin       | 18.8  | false            | Profit Margin (%)   |
  | Producto C | Sales_Volume        | 1450  | true             | Sales Volume (Units)|
  | Producto C | Growth_Rate         | 5.7   | false            | Growth Rate (%)     |
  ```
- **Resultado visual**: Gráfico con selectores para X e Y, burbujas proporcionales a Sales Volume, capacidad de alternar entre Market Share vs Profit Margin o Growth Rate vs Profit Margin dinámicamente.
- **Configuración aplicada**: Preselección Market Share (X) y Profit Margin (Y), Sales Volume como tamaño fijo, controles visibles a la derecha, tooltips con labels descriptivos.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; height: 565px; position: relative; overflow: hidden;">
  <iframe src="../../../assets/widgets_html/mas/multi_indicator_bubble_chart_01_interactive.html" 
          style="width: 100%; height: 475px; border: none; overflow: hidden; "
          loading="lazy"
          title="Ejemplo Interactivo del Multi-Indicator Bubble Chart">
  </iframe>
</div>

<style>
.widget-interactive-container iframe { min-height: 550px; }
</style>

## 8. Requerimientos Técnicos
- **Formato de salida**: Canvas/SVG híbrido para mejor performance con muchos elementos.
- **Librería recomendada**: D3.js v7+ o Chart.js v4+ para gráfico + HTML/CSS para controles.
- **Dependencias externas**: 
  - D3.js desde CDN (https://cdnjs.cloudflare.com/ajax/libs/d3/7.8.5/d3.min.js)
  - O Chart.js desde CDN (https://cdn.jsdelivr.net/npm/chart.js)
- **Compatibilidad**: Chrome, Firefox, Safari; completamente responsivo.
- **Performance**: Optimizado para hasta 50 elementos con recálculo eficiente en cambio de ejes.
- **Responsive breakpoints**: 
  - Desktop: >768px (controles a la derecha)
  - Tablet/Móvil: ≤768px (controles abajo del gráfico)
- **Validación en tiempo real**: Prevención de selección duplicada entre ejes X e Y.

## 9. Notas Adicionales
- **Estructura de datos normalizada**: Permite escalabilidad ilimitada de indicadores sin modificar esquema.
- **Indicador de tamaño obligatorio**: Exactamente un indicador debe tener `is_size_indicator = true` para funcionar correctamente.
- **Preselección inteligente**: Automáticamente selecciona los primeros dos indicadores no-tamaño como defaults para una experiencia inicial útil.
- **Validación cruzada**: Sistema de radio buttons con lógica que deshabilita opciones duplicadas entre ejes X e Y.
- **Labels descriptivos**: Campo `Label_Indicador` permite nombres user-friendly diferentes de los nombres técnicos.
- **Escalas dinámicas**: Recálculo automático de rangos min/max cuando se cambian los indicadores de los ejes.
- **UX responsivo**: Los controles se reposicionan automáticamente según el tamaño de pantalla para optimizar el espacio.
- **Performance optimizada**: Implementar debounce en cambios de indicadores para evitar recálculos excesivos.
- **Tooltips contextuales**: Información dinámica que cambia según los indicadores actualmente seleccionados en cada eje.
- **Accesibilidad**: Controles de radio button con labels claros y navegación por teclado para cumplir estándares WCAG.
- **Exportación inteligente**: Incluir información de configuración actual (ejes seleccionados) en datos exportados.