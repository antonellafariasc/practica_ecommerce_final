# Análisis de Datos de E-commerce

Este proyecto realiza un análisis completo de datos de un e-commerce, abarcando desde la integración de múltiples fuentes de datos hasta la segmentación de clientes mediante técnicas de Machine Learning.

## Tabla de Contenidos

- [Descripción del Proyecto](#descripción-del-proyecto)
- [Estructura de Archivos](#estructura-de-archivos)
- [Requisitos](#requisitos)
- [Preparación de los Datos](#preparación-de-los-datos)
- [Análisis Exploratorio](#análisis-exploratorio)
- [Procesamiento y Limpieza](#procesamiento-y-limpieza)
- [Transformaciones Numéricas](#transformaciones-numéricas)
- [Reducción de Dimensionalidad (PCA)](#reducción-de-dimensionalidad-pca)
- [Clustering de Clientes](#clustering-de-clientes)
- [Interpretación de Resultados](#interpretación-de-resultados)
- [Notas](#notas)

---

## Descripción del Proyecto

El objetivo es analizar el comportamiento de compra de los clientes de un e-commerce, identificar patrones y segmentar a los clientes en grupos homogéneos utilizando técnicas de reducción de dimensionalidad y clustering.

## Estructura de Archivos

- `analisis2.ipynb`: Notebook principal con todo el análisis y visualizaciones.
- `.gitignore`: Archivos y carpetas ignorados por git.
- `df_Customers.csv`, `df_Orders.csv`, `df_Payments.csv`, `df_Products.csv`, `df_Orderitems.csv`: Archivos de datos originales.
- `df_completo.csv`: Dataset integrado y procesado.

## Requisitos

- Python 3.8+
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

Instala los requisitos con:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

## Preparación de los Datos

1. **Carga de datos:**  
   Se cargan los archivos CSV de clientes, órdenes, pagos, productos y detalles de ítems.

2. **Integración:**  
   Se realiza un merge de todos los datasets usando claves como `customer_id`, `order_id` y `product_id`.

3. **Guardado:**  
   El dataset final integrado se guarda como `df_completo.csv`.

## Análisis Exploratorio

- Se exploran las primeras filas y la información general del dataset.
- Se identifican órdenes duplicadas y se analiza la cantidad de productos por orden.

## Procesamiento y Limpieza

- Se agrupan las órdenes para consolidar información de productos, cantidades y pagos.
- Se eliminan listas innecesarias en columnas como `product_id` y `product_category_name`.
- Se rellenan valores faltantes en `product_category_name` con `'desconocido'` y se asigna un identificador numérico especial.

## Transformaciones Numéricas

- Se convierten variables categóricas (`customer_city`, `customer_state`, `payment_type`, `order_status`, `product_category_name`) a variables numéricas usando `pd.factorize`.
- Se extrae el mes de compra de la fecha de la orden.
- Se verifica y trata la existencia de valores nulos.

## Reducción de Dimensionalidad (PCA)

- Se seleccionan variables numéricas relevantes para el análisis.
- Se estandarizan las variables.
- Se aplica PCA para reducir la dimensionalidad y retener el 95% de la varianza.
- Se visualiza la varianza explicada por cada componente principal.

## Clustering de Clientes

- Se determina el número óptimo de clusters usando el método del codo.
- Se aplica K-Means para segmentar a los clientes.
- Se visualizan los clusters en 2D usando los dos primeros componentes principales.
- Se analizan las características principales de cada cluster.

## Interpretación de Resultados

Se identifican y describen los siguientes segmentos de clientes:

- **Cluster 0:** Cliente estándar de São Paulo.
- **Cluster 1:** Comprador de alto valor fuera de São Paulo.
- **Cluster 2:** Cliente secundario de São Paulo.
- **Cluster 3:** Cliente mayorista o power buyer (B2B).

Cada segmento se interpreta en términos de comportamiento de compra, localización y valor para el negocio.

## Notas

- El análisis es reproducible y puede adaptarse a otros datasets de e-commerce con estructura similar.
- Los valores nulos y categorías desconocidas se manejan explícitamente para evitar errores en el modelado.
- El código está comentado y estructurado para facilitar su comprensión y modificación.

---

**Autor:**  
Antonella Farias
