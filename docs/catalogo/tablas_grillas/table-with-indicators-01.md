# Tabla con Indicadores

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Tabla que presenta datos con indicadores de estado y elementos visuales como barras o mini-gráficos para resaltar tendencias o cambios, con soporte para niveles jerárquicos (padre-hijo).
- **Identificador único**: `TABLE_WITH_INDICATORS_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Mostrar datos estructurados con indicadores visuales para facilitar la comparación y análisis de métricas o categorías, permitiendo explorar jerarquías de datos.
- **Casos de uso**:
    - Comparar el rendimiento de productos con metas establecidas, agrupados por categorías.
    - Analizar el progreso de tareas por departamento y subdepartamento.
    - Visualizar métricas de desempeño con cambios relativos, organizadas por regiones y sucursales.
- **Tipos de análisis soportados**: Descriptivo, comparativo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable categórica (ítem padre), 1 variable categórica (ítem hijo), 1 variable categórica (estado), 1 variable numérica (valor), 1 variable numérica (cambio).
    - Máximo: 5 variables categóricas (ítems padres), 5 variables categóricas por padre (ítems hijos), 2 variables categóricas (estado), 5 variables numéricas (valores), 5 variables numéricas (cambios).
    - Tipos de datos: Categórico (ítems, estados), numérico (valores, cambios).
  - **Estructura de datos** (grilla):

    | Ítem Padre      | Ítem Hijo          | Estado      | Valor     | Cambio   | Dirección Cambio |
    |-----------------|--------------------|-------------|-----------|----------|------------------|
    | Sales           | Product A          | On Track    | 1000      | 1100     | Up               |
    | Sales           | Product B          | Delayed     | 500       | -50      | Down             |
    | Marketing       | Campaign X         | On Track    | 300       | 30       | Up               |
    | Marketing       | Campaign Y         | Ahead       | 200       | 20       | Up               |

- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: Hasta 10 ítems padres con 5 hijos cada uno; recomendado 5 ítems padres con 3 hijos.

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Tabla con columnas para ítems padres e hijos, estado, valores, y elementos visuales como barras o mini-gráficos para cambios.
    - Soporte para jerarquías: ítems padres colapsables/expandibles para mostrar u ocultar ítems hijos.
    - Dimensiones: Mínimo 400x200 px, adaptable.
- **Categorías/Series**:
    - Máximo 10 ítems padres, cada uno con hasta 5 ítems hijos.
    - Exceso: Mostrar advertencia o paginación.
- **Opciones de personalización**:
    - Colores: Indicadores (ej. verde para positivo, rojo para negativo), barras o mini-gráficos (ej. verde para aumento, rojo para disminución).
    - Etiquetas: Mostrar nombres de ítems padres e hijos, estados, y valores.
    - Formato de valores: Numérico (enteros, decimales), moneda, porcentajes.
    - Ordenamiento: Por valor o alfabético (aplicable a padres e hijos).
    - Escalas: Longitud de barras proporcional al cambio absoluto.
    - Mini-gráficos: Opción para configurar una columna (ej. "Cambio") como mini-gráfico tipo butterfly, mostrando dos barras simétricas (positiva y negativa) para representar el cambio respecto a un eje central.
  - Jerarquía: Ícono o botón para expandir/colapsar ítems padres (ej. +/-).
- **Configuración de Dirección**:
    - Usar la columna "Dirección Cambio" para determinar la dirección de flechas o mini-gráficos (arriba para "Up", abajo para "Down").

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar ítems padres o hijos, estados.
    - Tooltips: Mostrar detalle del valor al pasar el cursor.
    - Expandir/Colapsar: Permitir a los usuarios expandir o colapsar ítems padres para ver u ocultar los ítems hijos.
    - Zoom: No aplica.
- **Eventos soportados**: Clic en fila para detalle, exportar como CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 10 ítems padres o 50 ítems hijos en total.
- **Casos no recomendados**: No usar para tendencias temporales (usar gráfico de líneas).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar el progreso de métricas organizadas por categorías jerárquicas.
- **Datos de entrada**:
  ```
  | Ítem Padre      | Ítem Hijo          | Estado      | Valor     | Cambio   | Dirección Cambio |
  |-----------------|--------------------|-------------|-----------|----------|------------------|
  | Sales           | Product A          | On Track    | 1000      | 1100     | Up               |
  | Sales           | Product B          | Delayed     | 500       | -50      | Down             |
  | Marketing       | Campaign X         | On Track    | 300       | 30       | Up               |
  | Marketing       | Campaign Y         | Ahead       | 200       | 20       | Up               |
  ```
- **Resultado visual**: Tabla con ítems padres "Sales" y "Marketing" colapsables; al expandir "Sales", se muestran "Product A" (✓ verde, mini-gráfico butterfly con barra verde hacia la derecha para 1100) y "Product B" (+ rojo, barra roja hacia la izquierda para -50). 
- **Configuración aplicada**: Verde para aumento, rojo para disminución, formato numérico, mini-gráfico butterfly en "Cambio", orden alfabético.

## 8. Requerimientos Técnicos
- **Dependencias**: HTML/CSS, Chart.js.
- **Formato de salida**: HTML.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Asegurar que las barras y mini-gráficos sean legibles y proporcionales al cambio.
- Permitir ajuste de grosor de barras o mini-gráficos.
- Asegurar que la funcionalidad de expandir/colapsar sea intuitiva y rápida.