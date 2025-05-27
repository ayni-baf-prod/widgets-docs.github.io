# Gráfico de Tacómetro

## 1. Nombre del Widget/Gráfico
- **Descripción breve**: Gráfico de tacómetro que muestra un valor en un rango definido con una aguja y colores indicadores.
- **Identificador único**: `GAUGE_CHART_01`.

## 2. Propósito y Casos de Uso
- **Objetivo**: Representar visualmente el cumplimiento o porcentaje de un indicador dentro de un rango predefinido.
- **Casos de uso**:
  - Mostrar el porcentaje de cumplimiento presupuestario (ej. 27% de "Budget Compliance").
  - Indicar el nivel de utilización de recursos.
  - Visualizar el estado de ejecución del presupuesto (ej. "Executed Budget" o "Status").
- **Tipos de análisis soportados**: Descriptivo, de estado.

## 3. Requerimientos de Datos
- **Variables/Indicadores**:
  - Mínimo: 1 variable numérica (valor), 1 variable numérica (rango máximo).
  - Máximo: 1 variable numérica (valor), 2 variables numéricas (rango mínimo, máximo), 3 rangos predefinidos (inicio-fin).
  - Tipos de datos: Numérico (valor, rango).
  - **Estructura de datos** (grilla):
    ```
    | Indicador       | Valor | Rango Mínimo | Rango Máximo | Rango 1 (Verde) | Rango 2 (Amarillo) | Rango 3 (Rojo) |
    |-----------------|-------|--------------|--------------|-----------------|--------------------|----------------|
    | Budget Compliance | 27%   | 0%           | 100%         | 0%-33%          | 34%-66%            | 67%-100%       |
    | Executed Budget | 60%   | 0%           | 100%         | 0%-30%          | 31%-70%            | 71%-100%       |
    | Status          | 60%   | 0%           | 100%         | 0%-30%          | 31%-70%            | 71%-100%       |
    ```
- **Fuente de datos**: Tablas SQL desde un datawarehouse. Los rangos deben venir preconfigurados desde el datawarehouse, ya que cada indicador puede tener diferentes rangos según el contexto (ej. cliente, área). Por ejemplo, "Budget Compliance" para Cliente 1 puede tener rangos verde 0%-33%, amarillo 34%-66%, rojo 67%-100%, mientras que para Cliente 2 puede ser verde 0%-10%, amarillo 11%-50%, rojo 51%-100%.
- **Volumen de datos**: Hasta 1 valor por instancia; recomendado único.

## 4. Configuración Visual
- **Estructura del gráfico**:
  - Disco semicircular con aguja y hasta 3 rangos de color.
  - Dimensiones: Mínimo 200x200 px, adaptable.
- **Categorías/Series**:
  - Máximo 1 valor por tacómetro.
  - Exceso: Mostrar advertencia.
- **Opciones de personalización**:
  - Colores: Hasta 3 rangos configurables con tonalidades personalizables (por defecto: verde, amarillo, rojo; el cliente puede elegir diferentes tonalidades, ej. verde claro, ámbar, rojo oscuro).
  - Etiquetas: Mostrar valor y rango.
  - Formato de valores: %, decimales.
  - Ordenamiento: No aplica.
  - Escalas: Rango definido (0-100% o según datawarehouse).

## 5. Interactividad
- **Funcionalidades interactivas**:
  - Filtros: No aplica, pero permite que otros filtros lo afecten.
  - Tooltips: Mostrar valor exacto al pasar el cursor.
  - Zoom: No aplica.
- **Eventos soportados**: Clic para detalle, exportar como PNG.

## 6. Limitaciones
- **Restricciones técnicas**: Rendimiento disminuye con actualizaciones frecuentes.
- **Casos no recomendados**: No usar para múltiples valores (usar gráfico de barras).

## 7. Ejemplo Práctico
- **Descripción**: Mostrar el cumplimiento presupuestario para diferentes clientes.
- **Datos de entrada**:
  ```
  | Indicador       | Valor | Rango Mínimo | Rango Máximo | Rango 1 (Verde) | Rango 2 (Amarillo) | Rango 3 (Rojo) |
  |-----------------|-------|--------------|--------------|-----------------|--------------------|----------------|
  | Budget Compliance (Cliente 1) | 27%   | 0%           | 100%         | 0%-33%          | 34%-66%            | 67%-100%       |
  ```
- **Resultado visual**: Tacómetro con aguja en 27%, rangos configurados según: verde 0%-33%, amarillo 34%-66%, rojo 67%-100%;. Imagen: [Placeholder para imagen de tacómetro].
- **Configuración aplicada**: Formato %, rangos verde/amarillo/rojo personalizados.

## Ejemplo Interactivo

<div class="widget-interactive-container" style="border: 1px solid #ccc; padding: 5px; border-radius: 10px; margin-bottom: 20px; min-height: 350px; position: relative;">
  <iframe src="../../../assets/widgets_html/GAUGE_CHART_01/gauge_chart_01_interactive.html" 
          style="width: 100%; height: 350px; border: none; overflow: hidden; "
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
- **Formato de salida**: SVG.
- **Compatibilidad**: Chrome, Firefox, Safari; responsivo.

## 9. Notas Adicionales
- Asegurar que los rangos sean dinámicos y cargados desde el datawarehouse.
- Validar que los rangos no se superpongan ni dejen huecos.