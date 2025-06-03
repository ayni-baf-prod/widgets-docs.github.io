# Gráfico de Radar para Evaluación Multidimensional

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de radar que representa un perfil multidimensional de un indicador (como productividad) a través de múltiples categorías, utilizando un polígono sombreado para facilitar la comparación visual.
- **Identificador único**: `RADAR_CHART_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Evaluar y comparar el rendimiento o perfil de un indicador en varias dimensiones (categorías) de manera integrada, permitiendo identificar fortalezas y debilidades relativas.
- **Casos de uso**: 
    - Mostrar la productividad (Communication, Delivery, Effectiveness, Knowledge, Skill set) por departamento en Recursos Humanos.
    - Comparar el perfil de competencias de empleados o equipos en RRHH.
    - Analizar el rendimiento de productos por características (calidad, precio, durabilidad) en finanzas o comercial.
    - Evaluar la eficiencia de procesos por factores (tiempo, costo, calidad) en operaciones.
    - Monitorear el balance de habilidades por proyecto (planificación, ejecución, comunicación) en gestión de proyectos.
    - En RRHH, se usa para análisis de habilidades o encuestas de satisfacción.
    - En marketing, ayuda a comparar el perfil de clientes o productos frente a competidores.
    - En deportes, se usa para evaluar estadísticas de jugadores (fuerza, velocidad, resistencia).

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Número mínimo y máximo de variables: 1 variable categórica (dimensiones), 1 variable numérica (valores por dimensión).
    - Tipos de datos soportados: Categórico (dimensiones), numérico (valores, típicamente en escala).
    - Estructura de datos: Ejemplo en formato de grilla:

    | Dimension     | Valor |
    |---------------|-------|
    | Communication | 3     |
    | Delivery      | 2     |
    | Effectiveness | 1     |
    | Knowledge     | 2     |
    | Skill set     | 3     |

- **Fuente de datos**: Tablas SQL desde un datawarehouse (ej. tabla de métricas por dimensión).
- **Volumen de datos**: Hasta 10 dimensiones; recomendado 5-7 dimensiones.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Polígono sombreado dentro de un radar con múltiples ejes, cada uno representando una dimensión y escalado (ej. 1-4).
    - Dimensiones recomendadas: 400x400 px, adaptable.
- **Categorías/Series**:
    - Número máximo de dimensiones: 10.
    - Comportamiento con exceso de dimensiones: Reducir a 10 o mostrar advertencia.
- **Opciones de personalización**:
    - Colores: Configurable para el polígono (ej. naranja para productividad).
    - Etiquetas: Mostrar valores en los vértices o en tooltips.
    - Formato de valores: Enteros o decimales en la escala.
    - Escalas: Personalizable por eje (ej. 1-5, 0-100).

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar dimensiones o departamentos específicos.
    - Tooltips: Mostrar valores exactos al pasar el cursor.
    - Zoom: No aplica.
- **Eventos soportados**: Clic en dimensión para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 10 dimensiones; difícil de interpretar con muchas categorías.
- **Casos no recomendados**: No usar para datos temporales (usar `LINE_CHART_01`).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar el perfil de productividad por departamento.
- **Datos de entrada**:
  ```
  | Dimension     | Valor |
  |---------------|-------|
  | Communication | 3     |
  | Delivery      | 2     |
  | Effectiveness | 1     |
  | Knowledge     | 2     |
  | Skill set     | 3     |
  ```
- **Resultado visual**: 
    - Gráfico de radar: Polígono naranja con vértices en 3 (Communication), 2 (Delivery), 1 (Effectiveness), 2 (Knowledge), 3 (Skill set).
- **Configuración aplicada**: Naranja para el polígono; escala 1-4.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 520px; position: relative;">
  <iframe src="../../../assets/widgets_html/mas/radar_chart_01_interactive.html" 
          style="width: 100%; height: 520px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo Radar">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 520px; /* Ajusta según la altura típica de tus widgets */
}
</style>

## 8. Requerimientos Técnicos
- **Dependencias**: HTML/CSS.
- **Formato de salida**: Canvas.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo (móvil, desktop).

## 9. Notas Adicionales
- Asegurar una escala consistente para todas las dimensiones.
- Considerar opción de superponer múltiples perfiles (ej. departamentos) con colores distintos.