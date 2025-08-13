# Gráfico Magic Quadrant

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de dispersión en cuatro cuadrantes que posiciona elementos según dos dimensiones de evaluación, permitiendo análisis comparativo y categorizaciones estratégicas.
- **Identificador único**: `MAGIC_QUADRANT_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Visualizar y categorizar elementos (empresas, productos, regiones, etc.) según dos criterios de evaluación, facilitando la identificación de líderes, desafiantes, visionarios y nichos específicos.
- **Casos de uso**:
    - Análisis de posicionamiento competitivo de proveedores tecnológicos.
    - Evaluación de performance de tiendas según ventas vs. satisfacción del cliente.
    - Categorización de productos según calidad vs. precio.
    - Análisis de regiones según rentabilidad vs. potencial de crecimiento.
- **Tipos de análisis soportados**: Descriptivo, comparativo, de posicionamiento estratégico.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable categórica (elemento), 2 variables numéricas (dimensión X, dimensión Y).
    - Máximo: 1 variable categórica (elemento), 2 variables numéricas (dimensión X, dimensión Y), 1 variable categórica opcional (año/período), 4 variables de texto (nombres de cuadrantes).
    - Escalas: Ambas dimensiones numéricas deben estar en escala de 0 a 100%.
  - **Estructura de datos** (grilla):

  | Elemento  | Dimension_X | Dimension_Y | Año  | Label_Eje_X | Label_Eje_Y | Cuadrante_TR | Cuadrante_TL | Cuadrante_BR | Cuadrante_BL |
  |-----------|-------------|-------------|------|-------------|-------------|--------------|--------------|--------------|--------------|
  | Microsoft | 89          | 72          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|
  | Tableau   | 86          | 89          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|
  | Qlik      | 73          | 84          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|
  | SAS       | 63          | 59          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|
  | SAP       | 68          | 49          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|
  | IBM       | 47          | 63          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|
  | Oracle    | 27          | 64          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|
  | Sisense   | 37          | 45          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|

- **Fuente de datos**: Tablas SQL desde un datawarehouse, CSV o Excel
- **Volumen de datos**: Hasta 25 elementos por gráfico para mantener legibilidad; agrupar excedentes en categorías "OTROS" por cuadrante.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Cuatro cuadrantes divididos por líneas sólidas en 50% de cada eje.
    - Grid de referencia con líneas cada 10% para mejor orientación visual.
    - Fondos de cuadrantes sutilmente diferenciados por colores.
    - Puntos de tamaño uniforme (radio 6px) posicionados según coordenadas X,Y.
    - Dimensiones: Mínimo 400x400 px, completamente adaptable y responsivo.
    - Breakpoints responsive: 768px (tablet), 480px (móvil).
- **Categorías/Series**:
   - Máximo 25 elementos (agrupar excedentes en "OTROS" y mostrar advertencia).
    - Exceso: Agrupar elementos excedentes por cuadrante en "OTROS" y mostrar advertencia.
- **Opciones de personalización**:
    - Colores: Paleta configurable para cada elemento y fondos sutiles diferenciados por cuadrante.
    - Etiquetas: Mostrar/ocultar nombres de elementos (automáticamente ocultos en pantallas <480px), valores de coordenadas.
    - Nombres de cuadrantes: Completamente configurables mediante campos TR (Top Right), TL (Top Left), BR (Button Right), BL (Button Left) en dataset.
    - Nombres de ejes: Configurables mediante campos Label_Eje_X y Label_Eje_Y en dataset.
    - Formato de valores: Porcentaje (%), decimales configurables.
    - Escalas: Fijas de 0% a 100% en ambos ejes con grid cada 10%.
    - Líneas divisorias: Sólidas, configurables en posición (por defecto en 50%).
    - Efectos hover: Aumento de tamaño y borde resaltado en puntos.

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Tooltips dinámicos: Formato "Elemento | Cuadrante | Eje_X: valor% | Eje_Y: valor%" que siguen el cursor.
    - Filtros opcionales: Selector temporal si el dataset incluye múltiples períodos.
    - Zoom: Capacidad de hacer zoom en áreas específicas del gráfico.
    - Efectos hover: Puntos se agrandan y resaltan con borde más grueso.
    - Redimensionamiento automático: Con debounce de 250ms para optimizar performance.
- **Eventos soportados**: Clic en elemento para resaltar, exportar como PNG/SVG/CSV.
- **Comportamiento temporal**: Si el dataset incluye múltiples años, calcular promedio automáticamente o permitir filtro temporal opcional.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 25 elementos visibles simultáneamente.
- **Casos no recomendados**: No usar para datos temporales continuos (usar gráfico de líneas), ni para más de dos dimensiones de evaluación.
- **Validaciones**: Ambas dimensiones deben estar en escala 0-100%. Elementos fuera del rango serán ajustados automáticamente.

## 7. Ejemplo Práctico
- **Descripción**: Mostrar el posicionamiento de proveedores de BI según capacidad de ejecución vs. visión estratégica en 2019.
- **Datos de entrada**:
  ```
  | Elemento  | Dimension_X | Dimension_Y | Año  | Label_Eje_X | Label_Eje_Y | Cuadrante_TR | Cuadrante_TL | Cuadrante_BR | Cuadrante_BL |
  |-----------|-------------|-------------|------|-------------|-------------|--------------|--------------|--------------|--------------|
  | Microsoft | 89          | 72          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|
  | Tableau   | 86          | 89          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|
  | Qlik      | 73          | 84          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|
  | SAS       | 63          | 59          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|
  | SAP       | 68          | 49          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|
  | IBM       | 47          | 63          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|
  | Oracle    | 27          | 64          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|
  | Sisense   | 37          | 45          | 2019 | Execution   | Vision      | Leaders      | Challengers  | Visionaries  | Niche Players|
  ```
- **Resultado visual**: Magic Quadrant con 4 cuadrantes claramente definidos, grid de referencia cada 10%, fondos sutilmente diferenciados, elementos posicionados según sus valores X,Y, tooltips informativos con formato "Elemento | Cuadrante | Eje: valor%", efectos hover suaves.
- **Configuración aplicada**: Ejes "Execution" (X) y "Vision" (Y), cuadrantes "Leaders", "Challengers", "Visionaries", "Niche Players", escala 0-100%, puntos uniformes con paleta profesional, responsive en 3 breakpoints.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; height: 760px; position: relative; overflow: hidden;">
  <iframe src="../../../assets/widgets_html/mas/magic_quadrant_01_interactive.html" 
          style="width: 100%; height: 760px; border: none; overflow: hidden; "
          loading="lazy"
          title="Ejemplo Interactivo del Magic Quadrant">
  </iframe>
</div>

<style>
.widget-interactive-container iframe { min-height: 760px; }
</style>

## 8. Requerimientos Técnicos
- **Formato de salida**: SVG para máxima escalabilidad.
- **Compatibilidad**: Chrome, Firefox, Safari; completamente responsivo.
- **Performance**: Optimizado para hasta 25 elementos simultáneos.
- **Responsive breakpoints**: 
  - Desktop: >768px (etiquetas y tooltips completos)
  - Tablet: 768px-480px (etiquetas reducidas)
  - Móvil: <480px (etiquetas ocultas, solo tooltips)
- **Redimensionamiento**: Debounce de 250ms para optimizar performance en resize.

## 9. Notas Adicionales
- Validar que los valores de las dimensiones estén en rango 0-100% antes del renderizado.
- Implementar algoritmo para evitar superposición de etiquetas cuando múltiples elementos están muy cercanos.
- Grid de referencia cada 10% mejora significativamente la orientación visual del usuario.
- Fondos de cuadrantes con colores sutiles (verde para Leaders, naranja para Challengers, azul para Visionaries, gris para Niche Players) facilitan la identificación rápida.
- Estructura de datos simplificada con nomenclatura abreviada: TR (Top Right), TL (Top Left), BR (Bottom Right), BL (Bottom Left).
- Tooltips con formato estandarizado: "Elemento | Cuadrante | Eje_X: valor% | Eje_Y: valor%" para consistencia.
- Permitir personalización de la posición de las líneas divisorias (por defecto 50%, pero configurable).
- Soportar múltiples períodos en el dataset con cálculo automático de promedios si no se especifica filtro temporal.
- Incluir leyenda configurable para explicar los cuadrantes y dimensiones.
- Implementar exportación de datos filtrados según la vista actual del usuario.
- Efectos de hover suaves (aumento de tamaño y borde resaltado) mejoran la experiencia de usuario sin ser intrusivos.
- En pantallas móviles (<480px), ocultar etiquetas automáticamente para mantener legibilidad, manteniendo solo tooltips interactivos.