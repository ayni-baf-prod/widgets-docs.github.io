# Gráfico de Mariposa comparación con Porcentaje %

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de barras horizontales simétricas que compara dos conjuntos de datos simultáneamente, extendiéndose desde un eje central para facilitar comparaciones directas.
- **Identificador único**: `BUTTERFLY_CHART_02`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Comparar visualmente dos conjuntos de datos dentro de cada grupo, destacando diferencias y similitudes de manera intuitiva.
- **Casos de uso**: 
    - Comparar payroll por género (Male/Female) por edad en Recursos Humanos.
    - Analizar ingresos por región (Norte/Sur) por producto en finanzas.
    - Evaluar producción por turno (Día/Noche) por línea en operaciones.
    - Comparar ventas por canal (Online/Offline) por mes en comercial.
    - Monitorear tareas completadas vs pendientes por proyecto en gestión de proyectos.
- **Tipos de análisis soportados**: Comparativo, descriptivo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Número mínimo y máximo de variables: 1 variable categórica (ej. grupos), 2 variables numéricas (valores de dos conjuntos).
    - Tipos de datos soportados: Categórico (grupos), numérico (valores).
    - Estructura de datos: Ejemplo en formato de grilla:

    | Grupo     | Male  | Female |
    |-----------|-------|--------|
    | 15-24     | 60%   | 50%    |
    | 25-34     | 76%   | 50%    |
    | 35-44     | 50%   | 60%    |
    | 45-54     | 60%   | 77%    |

- **Fuente de datos**: Tablas SQL desde un datawarehouse (ej. tabla de métricas por grupo y conjunto).
- **Volumen de datos**: Hasta 20 grupos; recomendado 5-10 grupos.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Barras horizontales simétricas que se extienden desde un eje central, con un conjunto a la izquierda y otro a la derecha.
    - Dimensiones recomendadas: 400x300 px, adaptable.
- **Categorías/Series**:
    - Número máximo de grupos: 20.
    - Comportamiento con exceso de grupos: Mostrar en categoría Otros.
- **Opciones de personalización**:
    - Colores: Configurables por conjunto (ej. azul para Male, rojo para Female).
    - Etiquetas: Mostrar valores al final de cada barra o en tooltips.
    - Formato de valores: Porcentajes, enteros, decimales.
    - Escalas: Simétrica en eje Y (valores), categórico en eje X (grupos).
    - Capacidad para habilitar scroll para ver todas las categorias cuando se condiciona el widget a espacios reducidos.
    - Eje central: Opcional con línea de referencia.

## 5. Interactividad
- **Funcionalidades interactivas**:
  - Filtros: Seleccionar grupos específicos.
  - Tooltips: Mostrar valores de cada conjunto al pasar el cursor.
  - Zoom: No aplica.
- **Eventos soportados**: Clic en barra para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 20 grupos.
- **Casos no recomendados**: No usar para más de 2 conjuntos (usar gráfico de barras apiladas).

## 7. Ejemplo Práctico
- **Descripción**: Comparar payroll por género por rango de edad.
- **Datos de entrada**:
  ```
  | Grupo     | Male  | Female |
  |-----------|-------|--------|
  | 15-24     | 60%   | 50%    |
  | 25-34     | 76%   | 50%    |
  | 35-44     | 50%   | 60%    |
  | 45-54     | 60%   | 77%    |
  ```
- **Resultado visual**: 
  - Gráfico de mariposa: 15-24 (azul 60% izquierda, rojo 50% derecha), 25-34 (azul 76% izquierda, rojo 50% derecha), etc.
- **Configuración aplicada**: Azul (Male), rojo (Female); formato porcentual.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 500px; position: relative;">
  <iframe src="../../../assets/widgets_html/comparacion/butterfly_chart_02_interactive.html" 
          style="width: 100%; height: 500px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo de Gráfico Mariposa">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 550px; /* Ajusta según la altura típica de tus widgets */
}
</style>

## 8. Requerimientos Técnicos

- **Formato de salida**: SVG
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo (móvil, desktop).

## 9. Notas Adicionales
- Asegurar simetría visual entre conjuntos.
- Considerar opción de resaltar diferencias con colores adicionales.