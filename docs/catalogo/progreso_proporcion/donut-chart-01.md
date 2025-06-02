# Gráfico de Dona

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de dona que muestra la distribución porcentual de ítems (ej. proyectos, tareas, productos, etc), con porcentajes y valores por colores.
- **Identificador único**: `DONUT_CHART_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Visualizar la proporción de ítems, permitiendo identificar rápidamente la distribución de categorías y su impacto.
- **Casos de uso**: 
    - Mostrar el estado de un conjunto de ítems (ej. proyectos en ejecución: Cumple, Retrasado, Adelantado).
    - Analizar la distribución de estados en métricas operativas (ej. órdenes de producción: Completadas, Pendientes, En Proceso).
    - Evaluar el desempeño general de un portafolio (ej. clientes: Activos, Inactivos, Nuevos) en contextos como finanzas, proyectos o ventas.
    - Mostrar la distribución de efectivo en bancos (ej. BBVA, BCP, Interbank).
    - Representar el porcentaje de facturas pagadas y no pagadas.
    - Analizar la contribución de categorías a un total (ej. ingresos por tipo).
- **Tipos de análisis soportados**: Descriptivo, comparativo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
  - Número mínimo y máximo de variables: 1 variable categórica (estado), 1 variable numérica (porcentaje o conteo de ítems por estado).
  - Tipos de datos soportados: Categórico (Categorías), numérico (porcentaje o valores).
  - Estructura de datos: Ejemplo en formato de grilla:
    ```
    | Estado         | Porcentaje | valores |
    |----------------|------------|---------|
    | Cumple         | 40%        | 40      |
    | Retrasado      | 20%        | 20      |
    | Adelantado     | 40%        | 40      |
    ```
- **Fuente de datos**: Tablas SQL desde un datawarehouse (ej. tabla de estados de ítems con conteos o porcentajes).
- **Volumen de datos**: Límite recomendado de 5 categorías de estado; máximo de 8 categorías antes de requerir agrupación.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Gráfico de dona con secciones para cada categoría o segmentos proporcionales a los porcentajes.
    - Colores indicadores: Azul (Cumple), Naranja (Retrasado), Celeste (Adelantado), configurables.
    - Leyenda con nombres de las categorias o segmentos y colores asociados.
    - Dimensiones recomendadas: 300x300 px, adaptable.
- **Categorías/Series**:
    - Número máximo de categorías: 8.
    - Comportamiento con exceso de categorías: Agrupar categorías menores en "Otros" con un color neutro(personalizable) .
- **Opciones de personalización**:
    - Colores: Personalizables por categoria usando una paleta (ej. azul, naranja, celeste).
    - Etiquetas: Mostrar/ocultar porcentajes de las secciones.
    - Formato de valores: Porcentajes o valores.
    - Ordenamiento: Por porcentaje (descendente) o alfabético por estado.
    - Orientación: Circular.

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar categorias específicos para enfocar.
    - Tooltips: Mostrar porcentaje y conteo al pasar el cursor por cada sección.
    - Zoom o desplazamiento: No aplica.
- **Eventos soportados**: Clic en sección para abrir detalle de la categoría, exportar datos como CSV.

## 6. Limitaciones
- **Restricciones técnicas**: No soporta más de 8 categorías por claridad visual; no recomendado para datos en tiempo real.
- **Casos no recomendados**: No usar para comparar valores numéricos absolutos (usar gráfico de barras).

## 7. Ejemplo Práctico
- **Descripción**: Visualizar la distribución de estados de un conjunto de ítems (ej. proyectos, órdenes, clientes).
- **Datos de entrada**:
  ```
  | Estado         | Porcentaje | Conteo |
  |----------------|------------|--------|
  | Cumple         | 40%        | 4      |
  | Retrasado      | 20%        | 2      |
  | Adelantado     | 40%        | 4      |
  ```
- **Resultado visual**: 
    - Gráfico de dona: Sección azul (Cumple, 40%), sección naranja (Retrasado, 20%), sección celeste (Adelantado, 40%).
    - Leyenda: Cumple (azul), Retrasado (naranja), Adelantado (celeste).
- **Configuración aplicada**: Colores azul, naranja, celeste; etiquetas de porcentaje visibles; ordenamiento por porcentaje descendente.

## 8. Requerimientos Técnicos
- **Formato de salida**: Canvas.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo (móvil, desktop).

## 9. Notas Adicionales
- Asegurar que los colores sean distinguibles para usuarios con daltonismo.
- Considerar integración futura con notificaciones basadas en estados críticos (ej. Retrasado).