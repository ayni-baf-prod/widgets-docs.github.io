# Gráfico de Tanque para Indicadores de Progreso

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico circular tipo tanque que muestra el progreso de un indicador (0% a 100%) con un efecto de llenado líquido, acompañado de un valor numérico y porcentaje, alcanzando llenado completo al 100%.
- **Identificador único**: `LIQUID_FILL_GAUGE_CHART_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Visualizar el nivel de cumplimiento o progreso de un indicador en una escala de 0% a 100%, utilizando un diseño intuitivo de tanque que se llena progresivamente.
- **Casos de uso**:
    - **Comercial**: Monitorear el porcentaje de meta de ventas alcanzada (ej. $750K de $1M, 75%) para incentivar al equipo.
    - **Finanzas**: Mostrar el nivel de fondo de emergencia utilizado (ej. 75% de $1M) para gestionar liquidez.
    - **Recursos Humanos**: Indicar el porcentaje de capacitación completada por empleados (ej. 75% de 100 horas) para planes de desarrollo.
    - **Operaciones**: Evaluar el nivel de inventario disponible (ej. 75% de capacidad) para optimizar la cadena de suministro.
    - **Gestión de Proyectos**: Rastrear el progreso de un proyecto (ej. 75% de hitos completados) para reportes de estado.
- **Uso en la industria de analítica**:
    - En comercial, mide metas de ventas o conversiones.
    - En finanzas, muestra niveles de liquidez o cumplimiento presupuestario.
    - En RRHH, evalúa avances en programas de capacitación.
    - En operaciones, indica niveles de almacenamiento o producción.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Número mínimo y máximo de variables: 1 variable numérica (valor actual), 1 variable numérica (valor objetivo), 1 variable categórica opcional (etiqueta).
    - Tipos de datos soportados: Numérico (valores), categórico (etiquetas).
    - Estructura de datos: Ejemplo en formato de grilla:

    | Indicador      | Valor Actual | Valor Objetivo | Porcentaje |
    |----------------|--------------|----------------|------------|
    | Ventas         | $750K        | $1M            | 75%        |

- **Fuente de datos**: Tablas SQL desde un datawarehouse (ej. tabla de métricas de progreso).
- **Volumen de datos**: 1 indicador por instancia; recomendado un solo indicador por gráfico.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Círculo con efecto de llenado líquido que sube desde la base, representando el porcentaje de progreso.
    - Dimensiones recomendadas: 200x200 px, adaptable.
- **Categorías/Series**:
    - Número máximo de indicadores: 1.
    - Comportamiento con exceso de indicadores: Mostrar un gráfico por indicador.
- **Opciones de personalización**:
    - Colores: Configurable para el líquido (ej. verde para 75%) y fondo.
    - Etiquetas: Mostrar valor, porcentaje y unidad dentro del tanque.
    - Formato de valores: Moneda, porcentaje, enteros.
    - Escalas: Progreso de 0% a 100%.

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar indicador específico.
    - Tooltips: Mostrar detalles de valor actual, objetivo y porcentaje.
    - Zoom: No aplica.
- **Eventos soportados**: Clic para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Limitado a un solo indicador por instancia; no apto para comparaciones múltiples.
- **Casos no recomendados**: No usar para datos temporales (usar `LINE_CHART_01`).

## 7. Ejemplo Práctico
- **Descripción**: Monitorear el progreso de ventas.
- **Datos de entrada**:
  ```
  | Indicador      | Valor Actual | Valor Objetivo | Porcentaje |
  |----------------|--------------|----------------|------------|
  | Ventas         | $750K        | $1M            | 75%        |
  ```
- **Resultado visual**: 
    - Gráfico de tanque: Llenado verde al 75%, con $750K y 75% visibles.
- **Configuración aplicada**: Verde para el líquido; formato moneda y porcentaje.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 220px; position: relative;">
  <iframe src="../../../assets/widgets_html/mas/liquid_fill_gauge_chart_01_interactive.html" 
          style="width: 100%; height: 220px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo Tanque">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 220px; /* Ajusta según la altura típica de tus widgets */
}
</style>

## 8. Requerimientos Técnicos
- **Formato de salida**: Canvas, SVG
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo (móvil, desktop).

## 9. Notas Adicionales
- Asegurar que el llenado sea proporcional al porcentaje (100% = tanque lleno).
- Considerar animación de llenado para mayor impacto visual.