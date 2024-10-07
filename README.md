# Análisis predictivo para la detección de fraudes en transacciones bancarias

## Antecedentes y visión general

SecureSwipe Solutions es una empresa de tecnología financiera en rápido crecimiento que presta servicios
 de procesamiento de pagos a comerciantes en línea y tiendas físicas de toda Europa. Fundada en 2020,
 la compañía ha experimentado un crecimiento exponencial, procesando cientos de miles de
 transacciones al mes. Sin embargo, con este crecimiento, SecureSwipe ha identificado un alarmante
 aumento en las transacciones fraudulentas, que está causando pérdidas financieras y dañando
 la reputación de la compañía entre sus clientes comerciales.

El actual sistema de detección del fraude en SecureSwipe se basa en reglas estáticas y está 
demostrando ser inadecuado para identificar patrones sofisticados de fraude. La empresa ha
 observado que los estafadores están adaptando sus técnicas más rápido de lo que las 
actualizaciones manuales de reglas pueden seguir. Esto ha dado lugar a falsos 
positivos (transacciones legítimas marcadas como fraudulentas) y falsos
 negativos (transacciones fraudulentas que no se detectan).

Para abordar estos desafíos, el liderazgo de SecureSwipe ha decidido implementar un sistema
 más avanzado y basado en datos de detección de fraude que utiliza 
técnicas de aprendizaje automático. Creen que al aprovechar la gran cantidad de datos 
de transacciones que han acumulado, pueden crear un modelo de detección de fraude más preciso y adaptable.

Este proyecto analiza los datos de transacciones para el entrenamiento de un modelo de aprendizaje automático, que
predicirá si una transacción es fraudulenta o legítima.

El conjunto de datos utilizado es de transacciones reales anonimizadas realizadas por usuarios en Europa. Aquí
se encuentran los [datos](https://www.kaggle.com/datasets/nelgiriyewithana/credit-card-fraud-detection-dataset-2023).

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
 método para evaluar nuestro modelo implicó el uso de la matriz de confusión. La matriz de confusión indicó 28 falsos positivos, un número relativamente pequeño
 en comparación con los verdaderos positivos (56,976). Esto implica la generalización del modelo. La siguiente image muestran la matriz de confusión.

![matriz-de-confusion](./matriz-de-confusion.png)


### Interpretabilidad

El modelo incluye capacidades de interpretabilidad al computar valores SHAP. Esto permitió descubrir que la característica más
 importante, por lejos, para predecir si una transacción es fraudulenta o legítima es 'V14' con un valor SHAP promedio global de 0.17, 
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

En función a los conocimientos adquiridos sobre los patrones de transacciones fraudulentas y legítimas, al entrenar un modelo predictivo
 con capacidades de generalización e interpretabilidad, usando árboles de decisión con aumento de gradiente (ADAG), implementado
 en XGBoost, a continuación se ofrecen algunas recomendaciones prácticas:

- Implementar modelo en producción: Basado en los resultados obtenidos el modelo es suficientemente robusto como para reemplazar el actual sistema de reglas 
estáticas. Se recomienda proceder con la implementación del modelo a nivel de producción para mejorar la detección de fraude y 
reducir las pérdidas financieras.

- Optimizar la interfaz con el cliente basada en interpretabilidad: Crear una interfaz clara y sencilla que explique las decisiones del modelo
 a los comerciantes y clientes. Por ejemplo, si una transacción es clasificada como sospechosa, el sistema debería poder exponer
 las principales razones de tal clasificación utilizando las características clave (como la 'V14') con explicaciones comprensibles. Esto es
 fundamental para mantener la confianza de los clientes cuando una transacción legítima es marcada como potencialmente fraudulenta.
Además se deberían implementar notificaciones en tiempo real para que los clientes puedan revisar inmediatamente las transacciones
 etiquetadas como sospechosas, y proporcionar un sistema eficiente para que puedan confirmar o refutar rápidamente la decisión.

- Proveer soporte y retroalimentación: Implementar un sistema de soporte activo para que los clientes de las compañías que se procesan los
 pagos, puedan reportar rápidamente problemas o dudas sobre el sistema de detección de fraude. Esta retroalimentación puede ser 
valiosa para mejorar tanto el modelo como la experiencia del cliente.

- Monitorear las métricas clave en producción: Aunque el modelo ha mostrado una alta tasa de precisión y sensibilidad, es fundamental
 monitorear continuamente su rendimiento en producción. Las amenazas de fraude evolucionan rápidamente, por lo que se
 recomienda implementar un sistema de monitorización que rastree métricas como la tasa de falsos positivos y negativos, la tasa
 de fraude detectado y las pérdidas financieras evitadas. 

- Reentrenar el modelo periódicamente: A medida que se acumulan más datos de transacciones, es importante
 reentrenar el modelo regularmente para que continúe aprendiendo de nuevos patrones de fraude y no se
 quede obsoleto. Se recomienda un ciclo de reentrenamiento periódicamente, por ejemplo, cada 3-6 meses,
 o cuando los indicadores clave de rendimiento comiencen a deteriorarse.

- Revisar manualmente los falsos negativos importantes: Aunque el modelo muestra una alta sensibilidad, es fundamental tener un equipo dedicado
 que revise manualmente las transacciones que el modelo no marca como sospechosas pero que los clientes o sistemas de auditoría
 identifiquen posteriormente como fraudulentas. Estos casos pueden proporcionar retroalimentación valiosa para ajustar el modelo.

- Enfocarse en las características clave: El análisis mostró que la característica ‘V14’ es la más relevante para la detección de fraude, con un
 valor SHAP promedio global de 0.17, marcadamente superior a las demás características. Se recomienda realizar un análisis más profundo
 de qué representa esta característica y cómo se puede mejorar su recolección de datos o representación en el sistema. Además, dado
 que la cantidad de dinero transferido (‘Amount’) fue identificada como la característica menos importante, se podría reconsiderar el
 peso que se le asigna a esta variable en otros sistemas de decisión.

- Explorar nuevas características: A medida que SecureSwipe crezca, es importante explorar la posibilidad de
 integrar nuevas características que podrían mejorar aún más la precisión del modelo. Esto podría incluir 
datos geográficos, patrones de comportamiento del usuario, o tiempos de transacción.

- Medir las pérdidas financieras evitadas al implementar el modelo: Una vez que el modelo esté en producción, se recomienda realizar un análisis
 detallado del impacto financiero de la implementación, midiendo las pérdidas evitadas debido a la detección activa de fraude. Esto permitirá
 calcular el retorno de inversión (ROI) del nuevo sistema. 

- Analizar los costos de falsos positivos: Dado que los falsos positivos también generan costos al bloquear transacciones legítimas, es
 importante analizar el impacto financiero de estas transacciones erróneamente clasificadas y ajustarlas en consecuencia.