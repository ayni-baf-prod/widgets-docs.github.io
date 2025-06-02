# Tabla con Indicadores

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Tabla que presenta datos con indicadores de estado, variaciones y elementos visuales como barras o mini-gráficos (butterfly chart), soportando hasta 3 niveles jerárquicos (padre-hijo-nieto), con reglas de negocio para colores, flechas y totalización basadas en umbrales, tipo de indicador y configuraciones personalizables.
- **Identificador único**: `TABLE_WITH_INDICATORS_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Mostrar datos estructurados con indicadores visuales que reflejen el cumplimiento y las variaciones respecto a presupuestos, permitiendo explorar jerarquías de hasta 3 niveles (padre-hijo-nieto) con colores, flechas y totalización contextualizados según el impacto en el negocio.
- **Casos de uso**:
  - Analizar el cumplimiento de activos y pasivos contra presupuestos, desglosado por categorías y subcategorías (ej. "Total Activo" → "Activo Corriente" → "Caja y Bancos").
  - Evaluar variaciones financieras por regiones, equipos o productos con indicadores visuales y totales.
  - Monitorear el desempeño financiero con umbrales y totalización configurables por tipo de indicador (incremental/decremental).
- **Tipos de análisis soportados**: Descriptivo, comparativo.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
  - Mínimo: 1 variable categórica (ítem padre), 1 variable categórica (ítem hijo), 1 variable categórica (ítem nieto), 1 variable numérica (actual), 1 variable numérica (presupuesto), 1 variable numérica (cumplimiento %), 1 variable categórica (tipo de indicador).
  - Máximo: 5 variables categóricas (ítems padres), 5 variables categóricas por padre (ítems hijos), 5 variables categóricas por hijo (ítems nietos), 1 variable numérica (actual), 1 variable numérica (presupuesto), 1 variable numérica (cumplimiento %), 1 variable numérica (umbral verde), 1 variable numérica (umbral amarillo), 1 variable numérica (umbral rojo), 1 variable numérica (variación), 1 variable numérica (anterior), 1 variable categórica (tipo de indicador).
  - Tipos de datos: Categórico (ítems, tipo de indicador), numérico (valores, porcentajes, umbrales, variaciones).
  - **Estructura de datos** (grilla de ejemplo):

    | Ítem Padre      | Ítem Hijo              | Ítem Nieto                        | Actual   | Presupuesto | Cumplimiento % | umbral verde (%) | umbral amarillo (%) | umbral rojo (%) | Variación | Anterior | Tipo de Indicador |
    |-----------------|-----------------------|-----------------------------------|----------|-------------|---------------|----------------------|---------------------|-----------------|-----------|----------|-------------------|
    | Total Activo    | Activo Corriente      | Caja y Bancos                    | 104,044  | 100,925     | 1.03          | 0.95                 | 80.00               | -               | (0.03)    | (2,700)  | INCREMENTAL       |
    | Total Activo    | Activo Corriente      | Cuentas por cobrar comerciales Relacionadas | 108,751  | 102,263     | 1.06          | 80.00                | 95.00               | 1.00            | 0.06      | 6,858    | DECREMENTAL       |

- **Totalización**:
  - Para ítems padres e hijos, el widget permite calcular:
    - **Valores numéricos** (Actual, Presupuesto, Anterior): Suma de todos los ítems hijos/nietos.
    - **Porcentajes** (Cumplimiento %, Variación): Promedio de todos los ítems hijos/nietos.
  - Configurable: Opción para habilitar/deshabilitar totalización por nivel (padre, hijo) y opciones para decidir si es un suma o promedio simple.
- **Reglas de Negocio para Colores de Cumplimiento %**:
  - Si `TIPO DE INDICADOR = INCREMENTAL`:
    - Si `Cumplimiento % < umbral amarillo`, color es rojo.
    - Si `umbral amarillo ≤ Cumplimiento % < umbral verde`, color es amarillo.
    - Si `Cumplimiento % ≥ umbral verde`, color es verde.
  - Si `TIPO DE INDICADOR = DECREMENTAL`:
    - Si `Cumplimiento % ≥ umbral rojo`, color es rojo.
    - Si `umbral amarillo ≤ Cumplimiento % < umbral rojo`, color es amarillo.
    - Si `Cumplimiento % < umbral amarillo`, color es verde.
  - Los umbrales (`umbral verde`, `umbral amarillo`, `umbral rojo`) son configurables por registro y se obtienen de las columnas correspondientes.
- **Reglas de Negocio para Flechas de Variación**:
  - Dirección de la flecha:
    - Si `Variación > 0`, flecha apunta hacia arriba (↑).
    - Si `Variación < 0`, flecha apunta hacia abajo (↓).
  - Color de la flecha:
    - Si `Variación > 0` (positiva) y `TIPO DE INDICADOR = INCREMENTAL`, color es verde (beneficioso).
    - Si `Variación > 0` (positiva) y `TIPO DE INDICADOR = DECREMENTAL`, color es rojo (perjudicial).
    - Si `Variación < 0` (negativa) y `TIPO DE INDICADOR = INCREMENTAL`, color es rojo (perjudicial).
    - Si `Variación < 0` (negativa) y `TIPO DE INDICADOR = DECREMENTAL`, color es verde (beneficioso).
- **Fuente de datos**: Tablas SQL desde un datawarehouse (ej. archivo CSV como `Balance Sheet.csv`).
- **Volumen de datos**: Hasta 5 ítems padres, con 5 hijos cada uno, y 5 nietos por hijo (125 ítems totales); recomendado 3 ítems padres, 3 hijos por padre, y 3 nietos por hijo (27 ítems totales).

## 4. Configuración Visual
- **Estructura del gráfico**:
  - Tabla con columnas para ítems padres, hijos y nietos, valores actuales, presupuestos, cumplimiento %, variaciones, y elementos visuales como flechas y mini-gráficos.
  - Soporte para jerarquías: ítems padres, hijos y nietos colapsables/expandibles.
  - Totalización: Ítems padres e hijos muestran valores totalizados (suma para valores numéricos, promedio para porcentajes), configurable.
  - Dimensiones: Mínimo 400x200 px, adaptable.
- **Categorías/Series**:
  - Máximo 5 ítems padres, cada uno con hasta 5 ítems hijos, y cada hijo con hasta 5 ítems nietos.
  - Exceso: agrupar en OTROS.
- **Opciones de personalización**:
  - Colores: 
    - `Cumplimiento %`: Verde, amarillo o rojo según las reglas de negocio basadas en `TIPO DE INDICADOR` y umbrales.
    - Flechas de `Variación`: Verde o rojo según las reglas de negocio basadas en `TIPO DE INDICADOR` y signo de la variación.
  - Totalización:
    - Habilitar/deshabilitar por nivel (padre, hijo).
    - Método de cálculo: Suma para valores numéricos, promedio para porcentajes.
  - Etiquetas: Mostrar nombres de ítems, valores, cumplimiento %, variación y tipo de indicador.
  - Formato de valores: Numérico (enteros, decimales), porcentajes, moneda.
  - Ordenamiento: Por cumplimiento %, variación o alfabético (aplicable a padres, hijos y nietos).
  - Escalas: Longitud de barras en mini-gráficos proporcional a la variación absoluta.
  - Mini-gráfico de mariposa (butterfly chart): Muestra la variación (`VAR.`) con desviaciones positivas (lado derecho) y negativas (lado izquierdo) desde un eje central (punto de equilibrio donde no hay variación). Permite identificar de un vistazo las partidas con mayores desviaciones, con el valor `ANTERIOR` como referencia para el eje central.
  - Jerarquía: Íconos o botones para expandir/colapsar ítems padres, hijos y nietos (ej. +/-).

## 5. Interactividad
- **Funcionalidades interactivas**:
  - Filtros: Seleccionar ítems padres, hijos, nietos, o tipos de indicador.
  - Tooltips: Mostrar detalle del cumplimiento %, variación y umbrales al pasar el cursor.
  - Expandir/Colapsar: Permitir a los usuarios expandir o colapsar ítems padres (para mostrar hijos), hijos (para mostrar nietos), y nietos (para mostrar detalles).
  - Zoom: No aplica.
- **Eventos soportados**: Clic en fila para detalle, exportar como CSV.

 ## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con más de 5 ítems padres, 25 ítems hijos o 125 ítems nietos en total.
- **Casos no recomendados**: No usar para tendencias temporales (usar gráfico de líneas).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar el cumplimiento y variaciones de activos, pasivos y patrimonio contra presupuestos, organizados en 3 niveles jerárquicos con totalización.
- **Datos de entrada**:
  ```
  | Ítem Padre      | Ítem Hijo             | Ítem Nieto                       | Actual   | Presupuesto |Cumplimiento % | umbral verde (%) | umbral amarillo (%) | umbral rojo (%) | Variación | Anterior | Tipo de Indicador |
  |-----------------|-----------------------|----------------------------------|----------|-------------|---------------|------------------|---------------------|-----------------|-----------|----------|-------------------|
  | Total Activo    | Activo Corriente      | Caja y Bancos                    | 104,044  | 100,925     | 1.03          | 0.95             | 80.00               | -               | (0.03)    | (2,700)  | INCREMENTAL       |
  | Total Activo    | Activo Corriente      | Cuentas x cobrar comerc. Relac.  | 108,751  | 102,263     | 1.06          | 80.00            | 95.00               | 1.00            | 0.06      | 6,858    | DECREMENTAL       |
  | Total Activo    | Activo Corriente      | Cuentas x cobrar comerc.Terceros | 96,337   | 101,236     | 0.95          | 80.00            | 95.00               | 1.00            | (0.04)    | (3,719)  | DECREMENTAL       |
  | Total Activo    | Activo Corriente      | Cuentas x cobrar Acc. y personal | 80,713   | 103,092     | 0.78          | 80.00            | 95.00               | 1.00            | (0.02)    | (2,505)  | DECREMENTAL       |
  | Total Activo    | Activo Corriente      | Otras cuentas x cobrar Relac.    | 100,334  | 108,069     | 0.93          | 80.00            | 95.00               | 1.00            | 0.07      | 7,721    | DECREMENTAL       |
  | Total Activo    | Activo Corriente      | Otras cuentas x cobrar Terceros  | 110,214  | 105,100     | 1.05          | 80.00            | 95.00               | 1.00            | 0.01      | 1,025    | DECREMENTAL       |
  | Total Activo    | Activo Corriente      | Otros Activos                    | 110,327  | 104,143     | 1.06          | 0.95             | 80.00               | -               | 0.01      | 1,428    | INCREMENTAL       |
  | Total Activo    | Activo No Corriente   | Inversiones financieras          | 115,014  | 104,451     | 1.10          | 0.95             | 80.00               | -               | 0.05      | 6,186    | INCREMENTAL       |
  | Total Activo    | Activo No Corriente   | Intangibles                      | 106,317  | 107,225     | 0.99          | 0.95             | 80.00               | -               | (0.06)    | (5,887)  | INCREMENTAL       |
  | Total Activo    | Activo No Corriente   | Propiedades, planta y equipo     | 105,272  | 107,628     | 0.98          | 0.95             | 80.00               | -               | 0.04      | 3,770    | INCREMENTAL       |
  | Total Pasivo    | Pasivo Corriente      | Sobregiros bancarios             | 106,730  | 108,378     | 0.98          | 0.95             | 80.00               | -               | (0.03)    | (2,802)  | INCREMENTAL       |
  | Total Pasivo    | Pasivo Corriente      | Tributos por pagar               | 108,449  | 96,555      | 1.12          | 80.00            | 95.00               | 1.00            | (0.03)    | (3,161)  | DECREMENTAL       |
  | Total Pasivo    | Pasivo Corriente      | Remuneraciones por pagar         | 108,649  | 107,832     | 1.01          | 80.00            | 95.00               | 1.00            | 0.02      | 2,491    | DECREMENTAL       |
  | Total Pasivo    | Pasivo Corriente      | Cuentas por pagar comerciales    | 101,023  | 113,819     | 0.89          | 80.00            | 95.00               | 1.00            | (0.06)    | (5,915)  | DECREMENTAL       |
  | Total Pasivo    | Pasivo Corriente      | Obligaciones financieras         | 103,683  | 98,813      | 1.05          | 80.00            | 95.00               | 1.00            | (0.10)    | (10,674) | DECREMENTAL       |
  | Total Pasivo    | Pasivo no Corriente   | Ganancia Diferida                | 103,160  | 109,922     | 0.94          | 0.95             | 80.00               | -               | 0.04      | 4,032    | INCREMENTAL       |
  | Total Patrimonio| Patrimonio            | Capital                          | 109,232  | 102,561     | 1.07          | 0.95             | 80.00               | -               | 0.04      | 4,153    | INCREMENTAL       |
  | Total Patrimonio| Patrimonio            | Reserva Legal                    | 99,862   | 110,839     | 0.90          | 0.95             | 80.00               | -               | (0.02)    | (2,064)  | INCREMENTAL       |
  | Total Patrimonio| Patrimonio            | Resultados Acumulados            | 107,687  | 107,596     | 1.00          | 0.95             | 80.00               | -               | 0.02      | 2,127    | INCREMENTAL       |
  | Total Patrimonio| Patrimonio            | Resultado del ejercicio          | 107,856  | 106,425     | 1.01          | 0.95             | 80.00               | -               | (0.02)    | (2,683)  | INCREMENTAL       |
  ```
- **Resultado visual**:   
  - **Indicadores visuales (ejemplos selectos)**:  
    - "Caja y Bancos": `Cumplimiento % = 1.03` (verde, ya que > 0.95 y tipo INCREMENTAL), flecha ↓ roja (variación -0.03, perjudicial para incremental).  
    - "Cuentas por cobrar comerciales Relacionadas": `Cumplimiento % = 1.06` (rojo, ya que > 1.00 y tipo DECREMENTAL), flecha ↑ verde (variación 0.06, beneficioso para decremental).  
    - "Tributos por pagar": `Cumplimiento % = 1.12` (rojo, ya que > 1.00 y tipo DECREMENTAL), flecha ↓ verde (variación -0.03, beneficioso para decremental).  
    - Mini-gráfico de mariposa para "Caja y Bancos": Barra izquierda (-2,700) en rojo, barra derecha (0) en gris (punto de equilibrio).  
    - Mini-gráfico de mariposa para "Obligaciones financieras": Barra izquierda (-10,674) en verde (beneficioso para decremental), barra derecha (0) en gris.  
- **Configuración aplicada**: Totalización habilitada, colores según reglas de negocio, flechas con colores contextuales, mini-gráfico butterfly mostrando desviaciones.

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 430px; position: relative;">
  <iframe src="../../../assets/widgets_html/INDICATOR_GRID_01/table-with-indicators-01.html" 
          style="width: 100%; height: 830px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo de la grilla">
  </iframe>
</div>


## 8. Requerimientos Técnicos

- **Formato de salida**: HTML.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Asegurar que los mini-gráficos de mariposa sean legibles y proporcionales a la variación.
- Permitir ajuste de grosor de barras o mini-gráficos.
- Verificar que las reglas de negocio para colores, flechas y totalización se apliquen correctamente en tiempo real según los datos de entrada.