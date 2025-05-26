# Progreso Circular

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Widget que muestra el progreso de un indicador del 0 al 100% mediante un círculo que se llena proporcionalmente, indicando el estado de completitud.
- **Identificador único**: `CIRCULAR_PROGRESS_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Visualizar el progreso de un indicador clave (ej. pago, cumplimiento) de manera intuitiva.
- **Casos de uso**:
  - Mostrar el porcentaje de cuentas por cobrar pagadas.
  - Indicar el avance de un proyecto o meta financiera.
  - Representar el porcentaje de presupuesto utilizado.
- **Tipos de análisis soportados**: Descriptivo, de progreso.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
  - Mínimo: 1 variable numérica (porcentaje de progreso).
  - Máximo: 1 variable numérica (porcentaje), 1 variable categórica (etiqueta).
  - Tipos de datos: Numérico (0-100%), categórico (etiqueta).
  - **Estructura de datos** (grilla):

    | Indicador         | Progreso (%) | Etiqueta    |
    |-------------------|--------------|-------------|
    | Accounts Receivable | 57.4         | Paid        |
    | Accounts Payable  | 42.6         | Paid        |

- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: 1 valor por widget.

## 4. Configuración Visual
- **Estructura del gráfico**:
  - Círculo con un segmento coloreado que representa el porcentaje de progreso, completándose al 100%.
  - Dimensiones: Mínimo 150x150 px, adaptable.
- **Categorías/Series**:
  - Máximo 1 valor por widget.
  - Exceso: No aplica.
- **Opciones de personalización**:
  - Colores: Segmento de progreso y fondo personalizables (ej. azul para progreso, gris para fondo).
  - Etiquetas: Mostrar porcentaje y etiqueta opcional (ej. "57.4% Paid").
  - Formato de valores: Porcentaje (0-100%).
  - Ordenamiento: No aplica.
  - Escalas: Proporcional al porcentaje (0-100%).

## 5. Interactividad
- **Funcionalidades interactivas**:
  - Filtros: No aplica, pero permite que otros filtros lo afecten.
  - Tooltips: Mostrar detalle del porcentaje al pasar el cursor.
  - Zoom: No aplica.
- **Eventos soportados**: Clic para detalle, exportar como PNG.

## 6. Limitaciones
- **Restricciones técnicas**: No aplica.
- **Casos no recomendados**: No usar para múltiples indicadores (usar gráfico de dona).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar el progreso de pago de cuentas por cobrar.
- **Datos de entrada**:
  ```
  | Indicador           | Progreso (%) | Etiqueta    |
  |---------------------|--------------|-------------|
  | Accounts Receivable | 57.4         | Paid        |
  ```
- **Resultado visual**: Círculo con 57.4% del segmento coloreado en azul, fondo gris, texto "57.4% Paid" en el centro. 
- **Configuración aplicada**: Color azul para progreso, fondo gris, etiquetas visibles.

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 280px; position: relative;">
  <iframe src="../../../assets/widgets_html/progreso/circular_progress_01_interactive.html" 
          style="width: 100%; height: 280px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo del Filtro">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 280px; /* Ajusta según la altura típica de tus widgets */
}
</style>


## 8. Requerimientos Técnicos
- **Dependencias**: HTML/CSS, SVG.
- **Formato de salida**: SVG.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Asegurar que el círculo sea legible y proporcional al porcentaje.
- Permitir ajuste de grosor del segmento de progreso.