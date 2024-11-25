# Análisis predictivo para la detección de fraudes en transacciones bancarias

## Antecedentes y visión general

Secure Swipe solutions, fundada en 2020, se dedica al manejo de pagos en comercios virtuales y 
físicos que abarcan Europa. Actualmente, tiene un desarrollo exponencial, al manejar cientos 
de miles de transacciones por mes. El problema que presenta la empresa es del aumento rápido 
de transacciones fraudulentas que provocan no solo pérdidas económicas, también la confianza de los clientes.

La empresa usa un sistema de detección basado en reglas estáticas, que demuestran ser inadecuados para 
identificar patrones sofisticados para realizar transacciones fraudulentas. Los estafadores encuentran 
en menor tiempo nuevas maneras de vencer al sistema. Esto produce falsos positivos (transacciones 
legítimas clasificados como fraudulentas) y falsos negativos (transacciones fraudulentas 
clasificados como legítimas).

La empresa ha decido actualizar el actual sistema con uno más avanzado que use los datos recolectados por
 la empresa para entrenar modelos basados en técnicas de aprendizaje automático. El objetivo es crear 
 un modelo más preciso y adaptable.

Este proyecto usa los datos de transacciones recogidos por la empresa para el entrenamiento de un modelo 
de aprendizaje automático, que clasificará transacciones para determinar si es legítima o fraudulenta.

Los datos utilizados son reales y provienen de transacciones anonimizadas hechas por usuarios en 
Europa. Aquí se encuentran los [datos](https://www.kaggle.com/datasets/nelgiriyewithana/credit-card-fraud-detection-dataset-2023).

### Estructura de datos y exploraciones iniciales

SecureSwipe Solutions tiene 568,630 transacciones de tarjetas de crédito realizadas por titulares de tarjetas europeos
 en 2023. Contiene 31 características, divididas en cuatro grupos. El primero identifica de manera única una transacción
 y solo incluye la columna `id`. El segundo grupo contiene casi todos los predictores (28 características) pero
 anonimizados (`V1`, `V2`,..., `V28`). El tercer grupo representa el monto de la transacción en euros (`Amount`). El grupo
 final es la característica objetivo (`Clase`) utilizando una etiqueta binaria que indica si la transacción es fraudulenta (1) o no (0).
La siguiente tabla ilustra esto:

| Característica | Propósito                                                                                   |
|----------------|---------------------------------------------------------------------------------------------|
| id             | Un identificador único para cada registro en el conjunto de datos                          |
| V1             | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V2             | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V3             | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V4             | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V5             | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V6             | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V7             | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V8             | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V9             | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V10            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V11            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V12            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V13            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V14            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V15            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V16            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V17            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V18            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V19            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V20            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V21            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V22            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V23            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V24            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V25            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V26            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V27            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| V28            | Características anonimizadas que representan varios atributos de transacción. (ej.: tiempo, localización, etc.) |
| Amount         | Monto de la transacción en euros                                                         |
| Class          | Etiqueta binaria que indica si la transacción es fraudulenta (1) o no (0)               |

El informe detallado se puede encontrar en [Kaggle](https://www.kaggle.com/code/christianmontenegro/detecci-n-de-fraudes-en-transacciones).
El modelo de proceso de estándar abierto usado es [CRISP-DM](https://www.datascience-pm.com/crisp-dm-2/).

## Resumen ejecutivo

### Visión general de descubrimientos

El modelo entrenado logra generalización al obtener excelentes resultados en diferentes métricas de rendimiento relevantes. El modelo también
tiene la capacidad de interpretabilidad al explicar como realiza la toma de decisiones para dar una predicción. En las siguientes
secciones se detallará esto.


### Rendimiento

El modelo obtuvo excelentes rendimientos, al utilizar AUC-ROC, sensibilidad, precisión y F1. Las puntuaciones fueron 0.99, 1, 0.99 y 0.99, respectivamente. Otro
 método para evaluar nuestro modelo implicó el uso de la matriz de confusión. La matriz de confusión indicó 18 falsos positivos, un número relativamente pequeño
 en comparación con los verdaderos positivos (56,976). Esto implica la generalización del modelo. La siguiente image muestran la matriz de confusión.

![matriz-de-confusion](./matriz-de-confusion.png)


### Interpretabilidad

El modelo incluye capacidades de interpretabilidad al computar valores SHAP. Esto permitió descubrir que la característica más
 importante, por lejos, para predecir si una transacción es fraudulenta o legítima es V14 con un valor SHAP promedio global de 0.18, 
esto representa un 212.5% más que la segunda característica más importante, 'V4' con 0.08. Es importante notar que la 
característica menos importante para la predicción objetiva del modelo es la cantidad de dinero transferido ('Amount'). La siguiente imagen
ilustra lo anterior.

![Explicacion-global-usando-shap](./Explicacion-global-usando-shap.png)


A nivel predictivo individual nos permite saber en más detalle una decisión particular para la confianza y transparencia del cliente. Cuando una
transacción es etiquetada como potencialmente fraudulenta, ser capaz de proveer una explicación clara y entendible puede ayudar a mantener
la confianza del cliente. El siguiente gráfico de cascada ilustra como el modelo toma una decisión para predecir correctamente que una transacción
es fraudulenta.

![grafico-de-cascada](./grafico-de-cascada.png)


## Recomendaciones y pasos futuros

En función a los conocimientos adquiridos sobre los patrones de transacciones fraudulentas y legítimas, al entrenar un modelo predictivo con capacidades de generalización e interpretabilidad, usando árboles de decisión con aumento de gradiente (ADAG), implementado en XGBoost, a continuación se ofrecen algunas recomendaciones prácticas:

- Implementar modelo en producción: Basado en los resultados obtenidos el modelo es suficientemente robusto como para reemplazar el actual sistema de reglas estáticas.

- Optimizar la interfaz con el cliente garantizado interpretabilidad: Implementar una interfaz  que explique decisiones a los clientes. Esto es fundamental para mantener la confianza de los clientes cuando una transacción legítima es marcada como fraudulenta.

- Proveer soporte y retroalimentación: Implementar un sistema de soporte activo para que los clientes de las compañías que se procesan los pagos, puedan reportar rápidamente problemas o dudas sobre el sistema de detección de fraude. La retroalimentación mejoraría tanto el modelo como la experiencia del cliente.

- Monitorear las métricas clave en producción: Aunque el modelo ha demostrado un excelente rendimiento, es de suma importancia monitorearlo en producción de manera continua. Las estrategias para realizar fraude evolucionan rápidamente, por eso es necesario monitorear métricas como la tasa de falsos positivos, falsos negativos y pérdidas financieras evitadas.

- Reentrenar el modelo periódicamente: Se debe entrenar el modelo regularmente para mantenerse a la par para identificar nuevos patrones de fraude. Se debe reentrenar cuando las métricas claves de rendimiento comiencen a deteriorarse considerablemente.

- Revisar manualmente los falsos negativos importantes: Aunque el modelo muestra una alta sensibilidad, es fundamental tener un equipo dedicado que revise manualmente las transacciones que el modelo no marca como sospechosas pero que los clientes o sistemas de auditoría identifiquen posteriormente como fraudulentas. Estos casos pueden proporcionar retroalimentación valiosa para ajustar el modelo.

- Enfocarse en las características clave: El análisis mostró que la característica V14 es la más relevante para la detección de fraude, con un valor SHAP promedio global de 0.18, marcadamente superior a las demás características. Se recomienda realizar un análisis más profundo de qué representa esta característica y cómo se puede mejorar su recolección de datos o representación en el sistema. Además, dado que la cantidad de dinero transferido (‘Amount’) fue identificada como la característica menos importante, se podría reconsiderar el peso que se le asigna a esta variable en otros sistemas de decisión.