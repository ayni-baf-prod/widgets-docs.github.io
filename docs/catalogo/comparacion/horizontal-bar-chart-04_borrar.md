# Gráfico de Barras Horizontales Apiladas

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de barras horizontales apiladas que muestra la contribución de múltiples categorías dentro de cada grupo, facilitando comparaciones entre grupos.
- **Identificador único**: `HORIZONAL_BAR_CHART_04`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Visualizar la distribución de valores dentro de categorías apiladas por grupo, permitiendo comparar la contribución total y relativa entre grupos.
- **Casos de uso**: 
    - Analizar la distribución de costos (salarios, bonos, horas extras) por departamento en finanzas.
    - Comparar el uso de recursos (materiales, mano de obra, energía) por línea de producción en operaciones.
    - Evaluar ventas por canal (online, físico, mayorista) por región en comercial.
    - Monitorear presupuesto por categoría (equipos, personal) por proyecto en gestión de proyectos.
- **Tipos de análisis soportados**: Comparativo, distributivo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Número mínimo y máximo de variables: 1 variable categórica (grupos), 2-5 variables numéricas (categorías apiladas).
    - Tipos de datos soportados: Categórico (grupos), numérico (valores).
    - Estructura de datos: Ejemplo en formato de grilla:

    | Grupo           | Categoría 1 (Salary) | Categoría 2 (Bonus) | Categoría 3 (Overtime) |
    |-----------------|----------------------|---------------------|------------------------|
    | Department 1    | 106                  | 90                  | 60                     |
    | Department 2    | 807                  | 160                 | 200                    |
    | Department 3    | 107                  | 70                  | 60                     |

- **Fuente de datos**: Tablas SQL desde un datawarehouse (ej. tabla de métricas por grupo y categoría).
- **Volumen de datos**: Hasta 20 grupos y 5 categorías; recomendado 10 grupos y 3 categorías.

## 4. Configuración Visual
- **Estructura del gráfico**:
  - Barras horizontales apiladas que representan la suma de categorías por grupo.
  - Dimensiones recomendadas: 400x300 px, adaptable.
- **Categorías/Series**:
  - Número máximo de categorías: 5.
  - Comportamiento con exceso de categorías: Agrupar en "Otros" con color neutro.
- **Opciones de personalización**:
  - Colores: Paletas Configurables por categoría (ej. azul, rojo, verde, ajustable).
  - Etiquetas: Mostrar valores en tooltips, opcionalmente en barras.
  - Formato de valores: Moneda (USD), enteros, decimales.
  - Escalas: Lineal en eje Y (valores), categórico en eje X (grupos).

## 5. Interactividad
- **Funcionalidades interactivas**:
  - Filtros: Seleccionar grupos o categorías específicas.
  - Tooltips: Mostrar valores de cada categoría y total al pasar el cursor.
  - Zoom: No aplica.
- **Eventos soportados**: Clic en barra para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 20 grupos.
- **Casos no recomendados**: No usar para tendencias temporales (usar gráfico de líneas).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar la distribución de payroll por departamento.
- **Datos de entrada**:
  ```
  | Grupo           | Salary | Bonus | Overtime |
  |-----------------|--------|-------|----------|
  | Department 1    | 106    | 90    | 60       |
  | Department 2    | 107    | 160   | 200      |
  | Department 3    | 107    | 70    | 60       |
  ```
- **Resultado visual**: 
  - Gráfico de barras apiladas: Department 1 (azul 100, rojo 50, verde 30).
  - Leyenda: Salary (azul), Bonus (rojo), Overtime (verde).
- **Configuración aplicada**: Colores azul, rojo, verde; formato numérico.

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
- **Formato de salida**: Canvas.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo (móvil, desktop).

## 9. Notas Adicionales
- Asegurar legibilidad de colores en fondos claros u oscuros.
- Considerar opción de mostrar porcentajes dentro de las barras.