# Gráfico de Barras Horizontales de Progreso con Indicadores de Estado

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de barras horizontales que compara un valor planificado (100%) con un valor ejecutado, mostrando el progreso en porcentaje y estados visuales (ej. On Track, Alert, Off Track) mediante colores indicadores.
- **Identificador único**: `HORIZONAL_BAR_CHART_03`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Comparar un valor ejecutado contra un valor planificado, destacando el progreso y el estado de cumplimiento con indicadores visuales para facilitar la identificación de desviaciones.
- **Casos de uso**: 
  - Comparar el avance real frente al planificado en cualquier tipo de métrica (ej. ventas alcanzadas vs. meta, horas trabajadas vs. estimadas, ingresos vs. presupuesto).
  - Identificar elementos que requieren atención (ej. métricas por debajo de lo esperado) en contextos como finanzas, proyectos, ventas o producción.
  - Monitorear el desempeño general de un conjunto de ítems (ej. regiones, equipos, productos).
- **Tipos de análisis soportados**: Descriptivo, comparativo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Número mínimo y máximo de variables: 1 variable categórica (ítem o categoría), 1 variable numérica (valor planificado), 1 variable numérica (valor ejecutado), 1 variable numérica (porcentaje de progreso), 1 variable categórica (estado).
    - Tipos de datos soportados: Categórico (ítem, estado), numérico (valor planificado, valor ejecutado, porcentaje).
    - Estructura de datos: Ejemplo en formato de grilla:

    | Ítem           | Valor Planificado | Valor Ejecutado | Progreso % | Estado       |
    |----------------|-------------------|-----------------|------------|--------------|
    | Ítem 1         | 100%              | 70%             | 70%        | Cumple       |
    | Ítem 2         | 100%              | 30%             | 30%        | No Cumple    |
    | Ítem 3         | 100%              | 60%             | 60%        | Alerta       |
    | Ítem 4         | 100%              | 50%             | 50%        | No Cumple    |
    | Ítem 5         | 100%              | 55%             | 55%        | Cumple       |

- **Fuente de datos**: Tablas SQL desde un datawarehouse (ej. tabla de métricas con valores planificados y ejecutados).
- **Volumen de datos**: Límite recomendado de 10 ítems; máximo de 20 ítems antes de requerir paginación.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Barras horizontales que representan el valor planificado (100% como línea base) y el valor ejecutado (longitud variable) para cada ítem.
    - Etiquetas de porcentaje de progreso junto a cada barra.
    - Colores indicadores: Verde (Cumple), Naranja (Alerta), Rojo (No Cumple), configurables según estado.
    - Dimensiones recomendadas: 400x300 px, adaptable.
- **Categorías/Series**:
    - Número máximo de categorías: 10 ítems.
    - Comportamiento con exceso de categorías: Agrupar en "OTROS".
- **Opciones de personalización**:
    - Colores: Verde, naranja, rojo para estados; personalizable por usuario.
    - Etiquetas: Mostrar/ocultar porcentaje de progreso.
    - Formato de valores: Porcentajes.
    - Ordenamiento: Por progreso % (ascendente/descendente) o alfabético por ítem.
    - Escalas: Lineal.
    - Orientación: Horizontal.

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar ítems específicos.
    - Tooltips: Mostrar detalles de valor planificado, valor ejecutado y estado al pasar el cursor.
    - Zoom o desplazamiento: No aplica.
- **Eventos soportados**: Clic en barra para abrir detalle del ítem, exportar datos como CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento puede disminuir con más de 10 ítems; no soporta datos en tiempo real.
- **Casos no recomendados**: No usar para análisis de tendencias temporales (usar gráfico de líneas).

## 7. Ejemplo Práctico
- **Descripción**: Comparar el avance de 5 ítems (ej. proyectos, regiones, productos) en términos de valor planificado vs ejecutado.
- **Datos de entrada**:
  ```
  | Ítem           | Valor Planificado | Valor Ejecutado | Progreso % | Estado       |
  |----------------|-------------------|-----------------|------------|--------------|
  | Ítem 1         | 100%              | 70%             | 70%        | Cumple       |
  | Ítem 2         | 100%              | 30%             | 30%        | No Cumple    |
  | Ítem 3         | 100%              | 60%             | 60%        | Alerta       |
  | Ítem 4         | 100%              | 50%             | 50%        | No Cumple    |
  | Ítem 5         | 100%              | 55%             | 55%        | Cumple       |
  ```
- **Resultado visual**: 
    - Barras horizontales: Ítem 1 (verde, 70%), Ítem 2 (rojo, 30%), Ítem 3 (naranja, 60%), Ítem 4 (rojo, 50%), Ítem 5 (verde, 55%).
    - Etiquetas: 70%, 30%, 60%, 50%, 55% junto a cada barra.
    
- **Configuración aplicada**: Colores verde, naranja, rojo; etiquetas de porcentaje visibles; ordenamiento por nombre de ítem.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 370px; position: relative;">
  <iframe src="../../../assets/widgets_html/comparacion/horizontal_bar_chart_03_interactive.html" 
          style="width: 100%; height: 370px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo de Heatmap">
  </iframe>
</div>

## 8. Requerimientos Técnicos
- **Formato de salida**: Canvas.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo (móvil, desktop).

## 9. Notas Adicionales
- Considerar integración futura con alertas automáticas basadas en estados (Cumple, Alerta, No Cumple).
- Optimizar rendimiento para dashboards con múltiples widgets.