# Gráfico de Sankey

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de flujo que muestra la transferencia de valores entre categorías mediante nodos y enlaces, destacando relaciones y magnitudes.
- **Identificador único**: `SANKEY_CHART_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Visualizar el flujo y distribución de recursos o valores entre categorías, como ingresos y gastos.
- **Casos de uso**:
    - Analizar el flujo de ingresos hacia ganancias y gastos operativos en un estado de resultados.
    - Mostrar la distribución de costos entre departamentos o productos.
- **Tipos de análisis soportados**: Descriptivo, de flujo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable categórica (origen), 1 variable categórica (destino), 1 variable numérica (valor).
    - Máximo: 5 variables categóricas (origenes/destinos), 2 variables numéricas (valor, variación % contra período anterior).
    - Niveles: Soporta de 2 a 7 niveles de flujo, definidos a nivel de datos.
  - **Estructura de datos** (grilla):

  | Origen             | Destino            | Valor (USD) | Variación % | Nivel Origen | Nivel Destino |
  |--------------------|--------------------|-------------|-------------|--------------|---------------|
  | Design             | Revenue            | 5,200M      | 8.2%        | 1            | 2             |
  | Constr             | Revenue            | 5,100M      | 3.1%        | 1            | 2             |
  | Tech               | Revenue            | 5,200M      | 0.0%        | 1            | 2             |
  | Revenue            | Gross Profit       | 11,000M     | 6.7%        | 2            | 3             |
  | Revenue            | Cost of Revenue    | 4,100M      | 8.3%        | 2            | 3             |
  | Gross Profit       | Operating Profit   | 7,300M      | 4.0%        | 3            | 4             |
  | Gross Profit       | Operating Expenses | 4,100M      | 0.5%        | 3            | 4             |
  | Operating Profit   | Net Profit         | 5,800M      | 0.3%        | 4            | 5             |
  | Operating Profit   | Tax                | 1,500M      | 7.4%        | 4            | 5             |
  | Operating Profit   | Other              | 1,800M      | 3.8%        | 4            | 5             |
  | Operating Expenses | G & A              | 1,300M      | 5.1%        | 4            | 5             |
  | Operating Expenses | R & D              | 1,700M      | 2.4%        | 4            | 5             |
  | Operating Expenses | S & M              | 1,100M      | 0.9%        | 4            | 5             |

- **Fuente de datos**: Tablas SQL desde un datawarehouse.
- **Volumen de datos**: Hasta 5 nodos por nivel (total máximo 35 nodos para 7 niveles); agrupar excedentes en "OTROS".

## 4. Configuración Visual
- **Estructura del gráfico**:
    - Nodos conectados por enlaces de ancho variable según el valor.
    - Niveles: Soporta de 2 a 7 niveles de flujo, definidos a nivel de datos.
    - Dimensiones: Mínimo 600x400 px, adaptable.
- **Categorías/Series**:
   - Máximo 5 nodos por nivel (agrupar excedentes en "OTROS").
    - Exceso: Agrupar nodos excedentes en "OTROS" y mostrar advertencia.
- **Opciones de personalización**:
    - Colores: Configuración flexible por nivel o nodo. Se pueden definir colores diferentes para cada nivel (ej. nivel 1 azul, nivel 2 verde) o colores únicos para cada nodo (ej. "Design" azul claro, "Constr" azul oscuro).
    - Etiquetas: Mostrar/ocultar valores, variaciones y nombres en nodos/enlaces.
    - Formato de valores: Moneda (USD), %, decimales.
    - Ordenamiento: Automático por flujo.
    - Escalas: Ancho proporcional al valor.

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Filtros: Seleccionar nodos o rangos de valores.
    - Tooltips: Mostrar valor, variación y descripción al pasar el cursor.
    - Zoom: En áreas específicas del gráfico.
- **Eventos soportados**: Clic en nodo/enlace para detalle, exportar como PNG/CSV.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 35 nodos o 30 enlaces.
- **Casos no recomendados**: No usar para datos temporales (usar gráfico de líneas).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar el flujo de ingresos y gastos en el estado de resultados de 2022 con variaciones.
- **Datos de entrada**:
  ```
  | Origen             | Destino            | Valor (USD) | Variación % | Nivel Origen | Nivel Destino |
  |--------------------|--------------------|-------------|-------------|--------------|---------------|
  | Design             | Revenue            | 5,200M      | 8.2%        | 1            | 2             |
  | Constr             | Revenue            | 5,100M      | 3.1%        | 1            | 2             |
  | Tech               | Revenue            | 5,200M      | 0.0%        | 1            | 2             |
  | Revenue            | Gross Profit       | 11,000M     | 6.7%        | 2            | 3             |
  | Revenue            | Cost of Revenue    | 4,100M      | 8.3%        | 2            | 3             |
  | Gross Profit       | Operating Profit   | 7,300M      | 4.0%        | 3            | 4             |
  | Gross Profit       | Operating Expenses | 4,100M      | 0.5%        | 3            | 4             |
  | Operating Profit   | Net Profit         | 5,800M      | 0.3%        | 4            | 5             |
  | Operating Profit   | Tax                | 1,500M      | 7.4%        | 4            | 5             |
  | Operating Profit   | Other              | 1,800M      | 3.8%        | 4            | 5             |
  | Operating Expenses | G & A              | 1,300M      | 5.1%        | 4            | 5             |
  | Operating Expenses | R & D              | 1,700M      | 2.4%        | 4            | 5             |
  | Operating Expenses | S & M              | 1,100M      | 0.9%        | 4            | 5             |
  ```
- **Resultado visual**: Gráfico de Sankey con 5 niveles, máximo 5 nodos por nivel, nodos "Revenue", "Gross Profit", "Operating Profit", "Net Profit", enlaces azules (ingresos), verdes (ganancias), rojos (gastos), valores en USD, variaciones en % para niveles 1 y 2.
- **Configuración aplicada**: Colores por nivel (nivel 1 azul, nivel 2 verde, etc.), formato moneda (USD), etiquetas con valores y variaciones visibles.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; height: 765px; position: relative; overflow: hidden;">
  <iframe src="../../../assets/widgets_html/mas/sankey_chart_01_interactive.html" 
          style="width: 100%; height: 675px; border: none; overflow: hidden; "
          loading="lazy"
          title="Ejemplo Interactivo del Diagrama Sankey">
  </iframe>
</div>

<style>
.widget-interactive-container iframe { min-height: 750px; }
</style>

## 8. Requerimientos Técnicos
- **Formato de salida**: SVG.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Optimizar disposición para evitar superposiciones de enlaces.
- Permitir personalización de anchura mínima de enlaces.
- Validar que los niveles estén bien definidos a nivel de datos.