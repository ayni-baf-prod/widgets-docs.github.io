# Gráfico de Embudo para Análisis de Conversiones

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de embudo que visualiza el flujo y la conversión de un proceso (como ventas) a través de etapas, mostrando la disminución de valores para identificar cuellos de botella o tasas de conversión.
- **Identificador único**: `FUNNEL_CHART_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Representar la progresión y conversión de un proceso en etapas (ej. funnel de ventas) para analizar la eficiencia y detectar áreas de mejora.
- **Casos de uso**:
    - **Comercial**: Monitorear el funnel de ventas (Prospects, Proposal, Negotiation, Wins) para optimizar la conversión de prospectos a clientes. En comercial, es clave para análisis de conversión y estrategias de cierre.
    - **Finanzas**: Analizar el flujo de inversión (Capital inicial, Evaluación, Aprobación, Desembolso) para evaluar la eficiencia en la asignación de fondos. En finanzas, ayuda a rastrear flujos de efectivo o aprobación de presupuestos.
    - **Recursos Humanos**: Evaluar el proceso de reclutamiento (Aplicaciones, Entrevistas, Ofertas, Contrataciones) para mejorar la retención de talento.
    - **Operaciones**: Rastrear el flujo de producción (Materias primas, Procesamiento, Ensamblaje, Envío) para identificar cuellos de botella. En operaciones, optimiza procesos de cadena de suministro.
    - **Marketing**: Medir el embudo de campañas (Impresiones, Clics, Registros, Compras) para optimizar el ROI.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
  - Número mínimo y máximo de variables: 1 variable categórica (etapas), 1 variable numérica (valores por etapa).
    - Tipos de datos soportados: Categórico (etapas), numérico (valores).
    - Estructura de datos: Ejemplo en formato de grilla:

    | Etapa         | Valor  |
    |---------------|--------|
    | Prospects     | $20M   |
    | Proposal      | $10M   |
    | Negotiation   | $8M    |
    | Wins          | $5M    |

- **Fuente de datos**: Tablas SQL desde un datawarehouse (ej. tabla de métricas por etapa).
- **Volumen de datos**: Hasta 10 etapas; recomendado 3-6 etapas.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Embudo con segmentos que disminuyen de ancho de arriba abajo, reflejando la conversión entre etapas.
    - Dimensiones recomendadas: 400x300 px, adaptable.
- **Categorías/Series**:
    - Número máximo de etapas: 10.
    - Comportamiento con exceso de etapas: Mostrar desplazamiento o agrupar.
- **Opciones de personalización**:
    - Colores: Configurables por etapa (ej. azul para Prospects, gris para Wins).
    - Etiquetas: Mostrar valores dentro de los segmentos o en tooltips.
    - Formato de valores: Moneda, porcentajes, enteros.
    - Escalas: Proporcional al valor en cada etapa.

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar etapas específicas.
    - Tooltips: Mostrar valores y tasas de conversión al pasar el cursor.
    - Zoom: No aplica.
- **Eventos soportados**: Clic en etapa para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 10 etapas; no apto para datos no jerárquicos.
- **Casos no recomendados**: No usar para distribuciones (usar `DONUT_CHART_01`).

## 7. Ejemplo Práctico
- **Descripción**: Monitorear el funnel de ventas.
- **Datos de entrada**:
  ```
  | Etapa         | Valor  |
  |---------------|--------|
  | Prospects     | $20M   |
  | Proposal      | $10M   |
  | Negotiation   | $8M    |
  | Wins          | $5M    |
  ```
- **Resultado visual**: 
    - Gráfico de embudo: Prospects ($20M, ancho mayor), Proposal ($10M), Negotiation ($8M), Wins ($5M, ancho menor).
- **Configuración aplicada**: Azul (Prospects), morado (Proposal), gris (Negotiation), claro (Wins); formato moneda.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 650px; position: relative;">
  <iframe src="../../../assets/widgets_html/mas/funnel_chart_01_interactive.html" 
          style="width: 100%; height: 650px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo Bubble">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 650px; /* Ajusta según la altura típica de tus widgets */
}
</style>

## 8. Requerimientos Técnicos
- **Dependencias**: HTML/CSS
- **Formato de salida**: Canvas.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo (móvil, desktop).

## 9. Notas Adicionales
- Asegurar que los valores disminuyan progresivamente para reflejar el embudo.
- Considerar opción de mostrar tasas de conversión entre etapas.