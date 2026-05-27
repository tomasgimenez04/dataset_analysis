# Amazon Products Sales 2025 - Análisis de Datos

Proyecto de análisis exploratorio de datos realizado en Python sobre un dataset de productos vendidos en Amazon. El objetivo principal fue limpiar, transformar y analizar información comercial para responder preguntas relacionadas con ingresos estimados, productos destacados y relación entre precio y calificación.

## Descripción del proyecto

Este proyecto forma parte de una práctica de introducción al análisis de datos. Se trabajó con el dataset **Amazon Products Sales 2025**, disponible en Kaggle, que contiene información sobre productos publicados en Amazon, incluyendo precio, calificación, cantidad de reseñas y compras realizadas durante el último mes.

A partir del dataset original, se realizó un proceso completo de análisis:

1. Carga del dataset.
2. Exploración inicial.
3. Selección de columnas relevantes.
4. Limpieza de datos.
5. Transformación de variables.
6. Cálculo de métricas.
7. Visualización de resultados.
8. Conclusiones.

## Objetivos del análisis

El trabajo busca responder principalmente estas preguntas:

- ¿Cuáles son los productos que más ingresos generaron el último mes?
- Dentro de los 5 productos con mayores ingresos, ¿qué porcentaje representa cada uno?
- ¿Qué productos tienen mejor rating promedio: los más baratos, los de precio medio o los más caros?

## Dataset utilizado

Dataset: **Amazon Products Sales Dataset - 42K Items 2025**

Fuente: Kaggle  
Archivo utilizado: `amazon_products_sales_data_uncleaned.csv`

El dataset original contiene aproximadamente **42.675 filas** y **16 columnas**. Para este análisis se seleccionaron las columnas necesarias para responder las preguntas planteadas.

Columnas utilizadas:

| Columna original | Columna renombrada | Descripción |
|---|---|---|
| `title` | `producto` | Nombre del producto |
| `rating` | `calificacion` | Calificación promedio del producto |
| `number_of_reviews` | `cantidad_de_reseñas` | Cantidad de reseñas |
| `bought_in_last_month` | `comprados_el_ultimo_mes` | Unidades compradas el último mes |
| `current/discounted_price` | `precio_actual` | Precio actual o con descuento |

## Tecnologías utilizadas

- Python
- Pandas
- Matplotlib
- Seaborn
- Google Colab
- Kaggle API

## Proceso realizado

### 1. Carga y exploración inicial

Se descargó el dataset desde Kaggle y se cargó en un DataFrame de Pandas. Luego se revisaron:

- Tamaño del dataset.
- Nombres de columnas.
- Tipos de datos.
- Cantidad de valores nulos.
- Cantidad de valores únicos.

### 2. Limpieza de datos

Como el dataset original no estaba completamente depurado, se realizó una limpieza para trabajar solo con datos útiles.

Acciones principales:

- Selección de columnas relevantes.
- Eliminación de duplicados.
- Eliminación de registros con valores nulos.
- Filtrado de valores no útiles en la columna de compras mensuales.
- Conversión de columnas de texto a valores numéricos.

Después de la limpieza y transformación, el dataset final quedó con aproximadamente **5.963 registros válidos** para el análisis.

### 3. Transformación de datos

Se transformaron las variables necesarias para poder analizarlas correctamente:

- `calificacion`: se extrajo el valor numérico desde textos como `"4.6 out of 5 stars"`.
- `cantidad_de_reseñas`: se eliminaron comas y se convirtió a número.
- `precio_actual`: se convirtió a número decimal.
- `comprados_el_ultimo_mes`: se transformaron valores como `6K+ bought in past month` a valores numéricos.
- `producto`: se acortaron nombres largos para mejorar la legibilidad de los gráficos.

También se creó una nueva columna:

```python
ingresos_mensuales = precio_actual * comprados_el_ultimo_mes
```

Esta variable permite estimar los ingresos generados por cada producto durante el último mes.

## Análisis realizado

### Productos con mayores ingresos estimados

Se calcularon los ingresos mensuales estimados para cada producto multiplicando el precio actual por la cantidad comprada en el último mes.

Luego se obtuvo el top 10 de productos con mayores ingresos.

Entre los productos destacados aparecieron:

- AMD RYZEN 7 9800X3D 8-Core
- Amazon Basics Multipurpose Copy Printer Paper
- HP OfficeJet Pro 8125e Wireless All-in-One
- HP Color Laserjet Pro MFP 3301sdw
- Sony WH-1000XM4 Wireless Premium Noise Cancelling

La visualización principal fue un gráfico de barras horizontal con los productos de mayor ingreso estimado.

### Participación porcentual del top 5

Se tomó el top 5 de productos con mayores ingresos y se generó un gráfico circular para visualizar qué porcentaje representaba cada uno dentro de ese grupo.

La conclusión fue que los ingresos estaban relativamente distribuidos entre los principales productos, sin que un único producto concentrara de forma extrema todo el ingreso del top 5.

### Relación entre precio y rating

Para analizar si los productos más caros tienen mejores calificaciones, se dividieron los productos en tres categorías de precio:

- Barato
- Medio
- Caro

Luego se calculó el rating promedio de cada categoría.

Resultados obtenidos:

| Rango de precio | Calificación promedio |
|---|---:|
| Barato | 4.55 |
| Medio | 4.45 |
| Caro | 4.37 |

La conclusión fue que, en promedio, los productos más baratos obtuvieron mejores calificaciones que los productos de precio medio y alto.

## Conclusiones principales

- Los productos con mayores ingresos estimados no necesariamente son los más caros, sino aquellos que combinan buen volumen de compras con un precio relevante.
- El top 5 de ingresos muestra una distribución relativamente equilibrada, sin una concentración absoluta en un solo producto.
- Los productos baratos presentan, en promedio, mejores calificaciones que los productos medios y caros.
- El precio parece influir en la percepción de satisfacción del usuario: los productos más económicos pueden generar mejores valoraciones si cumplen correctamente su función.
- La limpieza y transformación de datos fue una etapa clave, ya que varias columnas venían en formato texto y necesitaban estandarización para poder analizarlas.

## Estructura sugerida del repositorio

```text
amazon-products-sales-analysis/
├── Data_Analysis_Amazon_Sales.ipynb
├── README.md
└── data/
    └── amazon_products_sales_data_uncleaned.csv
```

> Nota: si el dataset es pesado o tiene restricciones de licencia, se recomienda no subirlo directamente al repositorio y dejar indicado el enlace a Kaggle.

## Cómo ejecutar el proyecto

### Opción 1: Google Colab

1. Abrir el archivo `.ipynb` en Google Colab.
2. Descargar el dataset desde Kaggle.
3. Cargar las credenciales de Kaggle si se utiliza la API.
4. Ejecutar las celdas en orden.

### Opción 2: entorno local

1. Clonar el repositorio:

```bash
git clone https://github.com/tu-usuario/amazon-products-sales-analysis.git
```

2. Instalar las librerías necesarias:

```bash
pip install pandas matplotlib seaborn
```

3. Abrir el notebook:

```bash
jupyter notebook Data_Analysis_Amazon_Sales.ipynb
```

4. Ejecutar las celdas en orden.

## Seguridad

No subir archivos con credenciales al repositorio, especialmente:

```text
kaggle.json
```

Si se utiliza la API de Kaggle, agregar este archivo al `.gitignore`:

```gitignore
kaggle.json
kaggle (1).json
```

## Autor

**Tomás Javier Giménez**

Proyecto realizado para la materia de Introducción al Análisis de Datos, en el marco de la Tecnicatura Universitaria en Programación.

## Estado del proyecto

Proyecto finalizado como análisis exploratorio inicial. Puede ampliarse incorporando nuevas métricas, análisis por categorías, segmentación de productos, modelos predictivos o dashboards interactivos.
