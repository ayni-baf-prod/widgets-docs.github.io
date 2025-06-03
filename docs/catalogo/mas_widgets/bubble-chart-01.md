# Gráfico de Burbujas para Análisis Multivariable

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de burbujas que representa tres variables simultáneamente: dos en los ejes X e Y (ej. ingresos vs. costos) y una tercera en el tamaño de las burbujas (ej. volumen de ventas), facilitando un análisis multivariable.
- **Identificador único**: `BUBBLE_CHART_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Visualizar y comparar múltiples dimensiones de datos (generalmente tres) para identificar correlaciones, patrones o excepciones en un conjunto de categorías.
- **Casos de uso**:
    - **Comercial**: Comparar productos por ingresos (eje X), costos (eje Y) y volumen de ventas (tamaño de burbuja) para optimizar la cartera de productos. En comercial, ayuda a identificar productos de alto impacto o subrendimiento.
    - **Finanzas**: Analizar inversiones por rentabilidad (eje X), riesgo (eje Y) y monto invertido (tamaño de burbuja) para decisiones de portafolio. En finanzas, se emplea para análisis de riesgo-retorno (ej. gráfico de Markowitz)
    - **Recursos Humanos**: Evaluar empleados por desempeño (eje X), satisfacción (eje Y) y antigüedad (tamaño de burbuja) para planes de retención.
    - **Operaciones**: Monitorear plantas por producción (eje X), costos operativos (eje Y) y capacidad (tamaño de burbuja) para eficiencia.
    - **Gestión de Proyectos**: Comparar proyectos por presupuesto (eje X), duración (eje Y) y recursos asignados (tamaño de burbuja) para priorización.


## 3. Requerimientos de Datos
- **Variables/Indicadores**:
  - Número mínimo y máximo de variables: 3 variables numéricas (eje X, eje Y, tamaño de burbuja), 1 variable categórica opcional (etiquetas).
  - Tipos de datos soportados: Numérico (valores), categórico (etiquetas).
  - Estructura de datos: Ejemplo en formato de grilla:

    | Categoría    | X (Ingresos) | Y (Costos) | Tamaño (Ventas) |
    |--------------|--------------|------------|-----------------|
    | Producto A   | 100          | 50         | 500             |
    | Producto B   | 80           | 60         | 300             |
    | Producto C   | 120          | 70         | 700             |

- **Fuente de datos**: Tablas SQL desde un datawarehouse (ej. tabla de métricas multivariable).
- **Volumen de datos**: Hasta 50 categorías; recomendado 10-20 categorías.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Burbujas posicionadas en un plano cartesiano (eje X, eje Y) con tamaño variable según una tercera variable.
    - Dimensiones recomendadas: 500x500 px, adaptable.
- **Categorías/Series**:
    - Número máximo de categorías: 50.
    - Comportamiento con exceso de categorías: Superposición controlada o paginación.
- **Opciones de personalización**:
    - Colores: Paletas Configurables por categoría (ej. azul, verde, rojo por producto).
    - Etiquetas: Mostrar nombres o valores en tooltips.
    - Formato de valores: Enteros, decimales.
    - Escalas: Lineal en ambos ejes, tamaño proporcional a la variable.

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar categorías o rangos de valores.
    - Tooltips: Mostrar valores de X, Y y tamaño al pasar el cursor.
    - Zoom: Ajustable para detalles.
- **Eventos soportados**: Clic en burbuja para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 50 categorías; superposición puede dificultar la lectura.
- **Casos no recomendados**: No usar para datos temporales (usar `LINE_CHART_01`).

## 7. Ejemplo Práctico
- **Descripción**: Comparar productos por ingresos, costos y volumen de ventas.
- **Datos de entrada**:
  ```
  | Categoría    | X (Ingresos) | Y (Costos) | Tamaño (Ventas) |
  |--------------|--------------|------------|-----------------|
  | Producto A   | 100          | 50         | 500             |
  | Producto B   | 80           | 60         | 300             |
  | Producto C   | 120          | 70         | 700             |
  ```
- **Resultado visual**: 
    - Gráfico de burbujas: Producto A (100, 50, tamaño 500), Producto B (80, 60, tamaño 300), Producto C (120, 70, tamaño 700).

- **Configuración aplicada**: Colores por producto; escala lineal.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 520px; position: relative;">
  <iframe src="../../../assets/widgets_html/mas/bubble_chart_01_interactive.html" 
          style="width: 100%; height: 520px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo Bubble">
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
- Asegurar un rango adecuado para el tamaño de burbujas para evitar superposición.
- Considerar opción de agregar una cuarta variable con colores.