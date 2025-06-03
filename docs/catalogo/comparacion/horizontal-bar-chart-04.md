# Gráfico de Barras Horizontales Apiladas al 100%

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de barras horizontales apiladas al 100% que muestra la distribución proporcional de un indicador a través de categorías, calculando automáticamente los porcentajes a partir de montos absolutos.
- **Identificador único**: `HORIZONAL_BAR_CHART_04`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Visualizar cómo se distribuye un indicador (como Total Payroll) a través de categorías (como departamentos), permitiendo comparar las proporciones relativas de cada categoría dentro de cada indicador, con cálculos automáticos de porcentajes a partir de montos.
- **Casos de uso**: 
    - Mostrar la distribución del Total Payroll por departamento (Department 1, 2, 3) en Recursos Humanos a partir de montos.
    - Analizar la composición de ingresos por región (Norte, Sur, Este) por tipo (ventas, servicios) en finanzas.
    - Evaluar el uso de recursos por tipo (materiales, mano de obra) por planta en operaciones.
    - Comparar ventas por canal (online, físico) por trimestre en comercial.
    - Monitorear presupuesto por categoría (equipos, personal) por proyecto en gestión de proyectos.
- **Tipos de análisis soportados**: Distributivo, comparativo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Número mínimo y máximo de variables: 1 variable categórica (indicadores), 1 variable categórica (categorías), 1 variable numérica (montos por categoría).
    - Tipos de datos soportados: Categórico (indicadores, categorías), numérico (montos).
    - Estructura de datos: Ejemplo en formato de grilla:

    | Indicador     | Department 1 | Department 2 | Department 3 |
    |---------------|--------------|--------------|--------------|
    | Total Payroll | 100          | 80           | 76           |
    | Salary        | 50           | 25           | 25           |
    | Bonus         | 45           | 30           | 25           |
    | Overtime      | 30           | 40           | 30           |

  - **Nota**: El widget calcula automáticamente los porcentajes dividiendo cada monto por la suma total del indicador (ej. Total Payroll: 100 + 80 + 76 = 256, luego 100/256 ≈ 39%, 80/256 ≈ 31%, 76/256 ≈ 30%).
- **Fuente de datos**: Tablas SQL desde un datawarehouse (ej. tabla de métricas con montos por indicador y categoría).
- **Volumen de datos**: Hasta 10 indicadores y 5 categorías; recomendado 4-6 indicadores y 3 categorías.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Barras horizontales apiladas al 100%, donde cada barra representa un indicador y se divide proporcionalmente por categoría según los porcentajes calculados a partir de montos.
    - Dimensiones recomendadas: 400x300 px, adaptable.
- **Categorías/Series**:
    - Número máximo de categorías: 5.
    - Comportamiento con exceso de categorías: Agrupar en "Otros" con color neutro.
- **Opciones de personalización**:
    - Colores: Paletas Configurables por categoría (ej. azul para Department 1, púrpura para Department 2, rojo para Department 3).
    - Etiquetas: Mostrar porcentajes calculados dentro de las barras o en tooltips (opcional mostrar montos originales).
    - Formato de valores: Porcentajes (calculados), montos originales opcionales en tooltips.
    - Escalas: Normalizada al 100% en eje Y, categórico en eje X (indicadores).

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar indicadores o categorías específicas.
    - Tooltips: Mostrar porcentajes calculados y montos originales al pasar el cursor.
    - Zoom: No aplica.
- **Eventos soportados**: Clic en barra para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 10 indicadores o 5 categorías; requiere montos positivos y no nulos.
- **Casos no recomendados**: No usar para valores absolutos sin normalización.

## 7. Ejemplo Práctico
- **Descripción**: Mostrar la distribución del Total Payroll y sus componentes por departamento a partir de montos.
- **Datos de entrada**:
  ```
  | Indicador     | Department 1 | Department 2 | Department 3 |
  |---------------|--------------|--------------|--------------|
  | Total Payroll | 100          | 80           | 76           |
  | Salary        | 50           | 25           | 25           |
  | Bonus         | 45           | 30           | 25           |
  | Overtime      | 30           | 40           | 30           |
  ```
- **Resultado visual**: 
    - Gráfico de barras horizontales apiladas al 100%: Total Payroll (azul ≈39%, púrpura ≈31%, rojo ≈30%), Salary (azul 50%, púrpura 25%, rojo 25%), etc.
- **Configuración aplicada**: Azul (Department 1), púrpura (Department 2), rojo (Department 3); formato porcentual calculado.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 480px; position: relative;">
  <iframe src="../../../assets/widgets_html/comparacion/horizontal_bar_chart_04_interactive.html" 
          style="width: 100%; height: 480px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo de Gráfico de barras horizontal 4">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 480px; /* Ajusta según la altura típica de tus widgets */
}
</style>

## 8. Requerimientos Técnicos
- **Dependencias**: HTML/CSS
- **Formato de salida**: Canvas.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo (móvil, desktop).

## 9. Notas Adicionales
- Asegurar que los montos sumen un valor válido por indicador para evitar errores de cálculo.
- Considerar opción de mostrar el total absoluto del indicador en la leyenda o tooltip.