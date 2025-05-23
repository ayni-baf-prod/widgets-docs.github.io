# Selector de Rango de Fechas

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Widget que permite al usuario seleccionar un rango de fechas para filtrar datos en el dashboard.
- **Identificador único**: `DATE_RANGE_PICKER_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Facilitar la filtración de datos por un intervalo de tiempo definido por el usuario.
- **Casos de uso**:
    - Filtrar gastos totales entre julio y octubre de 2021.
    - Analizar ingresos en un rango de fechas específico.
- **Tipos de análisis soportados**: Filtrado temporal.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
    - Mínimo: 1 variable temporal (fecha de inicio), 1 variable temporal (fecha de fin).
    - Máximo: No aplica (solo 2 variables temporales).
    - Tipos de datos: Temporal (fechas).
  - **Estructura de datos** (grilla): Define el rango de fechas que se mostrará por defecto al cargar el widget.
    ```
    | Parámetro        | Tipo   | Formato    | Ejemplo    | Descripción                           |        
    |------------------|--------|------------|------------|---------------------------------------|
    | defaultStartDate | String | YYYY-MM-DD | 2021-07-05 | Fecha de inicio del rango por defecto |
    | defaultEndDate   | String | YYYY-MM-DD | 2021-10-15 | Fecha de fin del rango por defecto    |



    ```
O como un objeto JSON de configuración:
```json
  {
    "defaultStartDate": "2021-07-05",
    "defaultEndDate": "2021-10-15"
  }
```
- **Fuente de datos**: No aplica directamente para las opciones del selector (ya que son fechas), pero sí para los datos que serán filtrados por este widget, los cuales deben provenir de tablas SQL desde un datawarehouse con campos de fecha relacionables.s.

- **Volumen de datos**: El calendario puede mostrar un amplio rango de años. La restricción de "Hasta 365 días por rango; recomendado 90 días" se refiere al rango seleccionado para optimizar el rendimiento de las consultas que usan este filtro, no a las opciones del calendario en sí.

## 4. Configuración Visual
- **Estructura del componente**:
    - Al activarse, el widget muestra un panel (popup) que contiene:
        - Dos campos de entrada de fecha (calendario) con etiquetas "FROM" y "TO".
        - Al hacer clic en el campo de texto o en el ícono de calendario asociado, se despliega un calendario interactivo para la selección visual de la fecha.
        - Una sección con botones de rangos predefinidos ('Last Week', 'Last Month', 'Last Year'), las mismas que tienen que ser configurables. Los criterios para los usuarios finales puede ser diferentes, para algunos last month puede ser los últimos 30 dias, para otros puede ser del 1 al 30 del mes anterior.
    - Dimensiones: Ancho adaptable, altura 100px.
- **Categorías/Series**:
    - Máximo 1 rango de fechas.
    - Exceso: Mostrar advertencia.
- **Opciones de personalización**:
    - Configurar el formato de cómo se muestra el rango en el campo principal cuando está cerrado (ej. "MMMM DD - DD, YYYY" vs. "DD/MM/YY - DD/MM/YY").
    - Configurar el formato para los campos FROM/TO dentro del popup (ej. "dd.mm.yyyy")
    - Configurar lista de rangos predefinidos (presets)
    - Opciones para restringir el rango total seleccionable en los calendarios (ej. no permitir fechas futuras, o no permitir fechas anteriores a cierto punto).
    - Colores: Fondo y texto personalizables.
    - Etiquetas: Mostrar "FROM" y "TO".
    - Formato de valores: Fecha (dd.mm.yyyy, mm/yyyy, etc.).
    - Ordenamiento: Cronológico.
    - Escalas: No aplica.

## 5. Interactividad
- **Funcionalidades interactivas**:
    - Selección: Los calendarios para 'Fecha Desde' y 'Fecha Hasta' están sincronizados: la 'Fecha Desde' no puede ser posterior a la 'Fecha Hasta', y viceversa.
    - Botones de Presets: Los botones de rangos predefinidos ('Last Week', 'Last Month', 'Last Year') actualizan automáticamente los campos 'Fecha Desde' y 'Fecha Hasta' y el display principal del widget.
    - Filtros dinámicos: Actualizar otros widgets según el rango seleccionado.
    - Tooltips: No Aplica.
    - Cierre del Popup: Cierra al seleccionar un rango predefinido o al hacer clic fuera del área del popup y del campo de display principal.
- **Eventos soportados**: Cambio de fechas para actualizar el dashboard.
- **Impacto en el Dashboard**: Al seleccionar un rango de fechas, se espera que todos los widgets del dashboard configurados para responder a filtros temporales (ej. gráficos de series de tiempo, KPIs con tendencia, tablas de transacciones) actualicen sus datos para reflejar únicamente el período seleccionado.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con rangos mayores a 365 días.
- **Casos no recomendados**: No usar para selección de fechas individuales (usar dropdown).

## 7. Ejemplo Práctico
- **Descripción**: Filtrar datos de gastos entre julio y octubre de 2021.
- **Datos de entrada**:
  ```
  | Fecha Inicio  | Fecha Fin    |
  |---------------|--------------|
  | 05.07.2021    | 15.10.2021   |
  ```
- **Resultado visual**: Estado Cerrado: Un campo de display con la etiqueta 'DATE' a la izquierda, mostrando el rango 'July 05 - October 15, 2021' y un ícono de calendario a la derecha.
Estado Abierto (al hacer clic): Un popup aparece debajo mostrando campos 'FROM' (con '05.07.2021') y 'TO' (con '15.10.2021'), cada uno con su ícono de calendario, y debajo botones para 'Last Week', 'Last Month', 'Last Year'. Fondo blanco, texto principal oscuro.
- **Configuración aplicada**: Formato dd.mm.yyyy, fondo blanco, texto negro.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 350px; position: relative;">
  <iframe src="../../../assets/widgets_html/DATE_RANGE_PICKER_01/date_range_picker_01_interactive.html" 
          style="width: 100%; height: 350px; border: none; overflow: auto;"
          loading="lazy"
          title="Ejemplo Interactivo del Filtro">
  </iframe>
</div>

<style>
/* Opcional: Para asegurar que el iframe se ajuste bien si el contenido es más alto */
.widget-interactive-container iframe {
    min-height: 350px; /* Ajusta según la altura típica de tus widgets */
}
</style>

## 8. Requerimientos Técnicos
- **Formato de salida**: HTML/CSS.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Sincronizar con el datawarehouse para rangos válidos.