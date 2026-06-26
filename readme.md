# EP03 - Proyecto de Data Mining

Proyecto de minería de datos orientado al análisis de abandono parcial de clientes residenciales en una empresa de telecomunicaciones.

## Objetivo

Identificar patrones asociados al abandono de clientes residenciales y generar recomendaciones de negocio mediante técnicas supervisadas, no supervisadas y reglas de asociación.

El análisis busca apoyar decisiones de retención, priorización comercial y diseño de campañas focalizadas.

## Segmento analizado

El proyecto se enfoca exclusivamente en clientes del segmento **Residencial**, debido a que representa la mayor parte de la base de clientes y constituye un grupo relevante para acciones de fidelización.

## Contenido del repositorio

* `EP03.ipynb`: notebook principal del proyecto.
* `docs/`: entregables, pauta, documentación de apoyo y descripción del trabajo.
* `data/`: datos originales utilizados en el análisis.
* `data/processed/`: datasets y artefactos generados durante el procesamiento y modelamiento.
* `outputs/presentacion/`: gráficos y tablas generados para apoyar la presentación final.

## Metodología

El proyecto sigue las primeras fases de la metodología CRISP-DM:

1. Comprensión del negocio.
2. Comprensión de los datos.
3. Preparación de los datos.
4. Modelamiento.
5. Evaluación e interpretación de resultados.

## Preparación de datos

Durante la preparación se realizaron las siguientes acciones:

* Filtro del segmento Residencial.
* Eliminación de duplicados.
* Revisión de valores nulos.
* Exclusión de variables constantes o completamente nulas.
* Exclusión de variables con fuga de información, como `ABA_*` y variables `ABANDONO_*` distintas del target.
* Transformación de variables tipo lista en indicadores binarios.
* Imputación de valores faltantes.
* Separación entre variables predictoras y variable objetivo.

La variable objetivo utilizada fue:

* `ABANDONO_FULL`

## Modelos implementados

### Modelos supervisados

Se evaluaron modelos de clasificación para predecir abandono:

* Regresión Logística balanceada.
* Árbol de Decisión balanceado.
* Naive Bayes.
* SVM lineal balanceado como modelo adicional investigado.

Las métricas utilizadas fueron:

* Accuracy.
* Precision.
* Recall.
* F1-Score.
* ROC-AUC.
* PR-AUC.
* Matriz de confusión.

El modelo seleccionado fue la **Regresión Logística balanceada**, debido a su equilibrio entre Recall, F1-Score e interpretabilidad.

### Modelos no supervisados

Se aplicaron modelos de segmentación para identificar perfiles de clientes:

* K-Means.
* Clustering Jerárquico.

K-Means fue utilizado como modelo operativo sobre la base completa, mientras que el Clustering Jerárquico se aplicó sobre una muestra representativa por costo computacional.

### Reglas de asociación

Se implementaron reglas de asociación tipo Apriori sobre servicios contratados y servicios vigentes.

Las métricas utilizadas fueron:

* Soporte.
* Confianza.
* Lift.

El objetivo fue identificar combinaciones de servicios útiles para estrategias de paquetización, fidelización y venta cruzada.

## Principales resultados

El análisis mostró que el abandono residencial es un problema desbalanceado, con una baja proporción de clientes que abandonan.

La Regresión Logística balanceada permitió detectar una proporción relevante de abandonos reales, por lo que se propone su uso como herramienta de priorización comercial y no como regla automática de contacto masivo.

La segmentación permitió identificar grupos de clientes con distinto nivel de riesgo, especialmente clientes con menor paquetización y menor antigüedad relativa.

Las reglas de asociación mostraron patrones relevantes entre servicios como TV, Telefonía, SVA, TNT Sport y Alarmcom, los cuales pueden apoyar campañas de empaquetamiento y retención.

## Recomendaciones de negocio

A partir de la combinación de modelos supervisados, clusters y reglas de asociación, se proponen campañas como:

* Campañas para clientes de Internet con baja paquetización y mayor riesgo.
* Ofertas de empaquetamiento entre Internet, TV y Telefonía.
* Pilotos de beneficios asociados a servicios complementarios.
* Acciones preventivas para clientes consolidados con riesgo elevado.

## Ejecución

Abrir y ejecutar el notebook principal:

```bash
jupyter notebook EP03.ipynb
```

También puede ejecutarse desde VS Code utilizando un kernel de Python compatible.

## Librerías principales

* pandas
* numpy
* matplotlib
* scikit-learn

## Nota

Los modelos desarrollados deben interpretarse como herramientas de apoyo a la toma de decisiones. Su objetivo principal es priorizar clientes y orientar campañas, no reemplazar el juicio comercial ni automatizar decisiones de contacto sin evaluación previa.
