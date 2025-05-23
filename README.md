# Prediccion-de-Churn-en-Telecomunicaciones
Al operador de telecomunicaciones Interconnect le gustaría poder pronosticar su tasa de cancelación de clientes. Si se descubre que un usuario o usuaria planea irse, se le ofrecerán códigos promocionales y opciones de planes especiales.

### Servicios de Interconnect

Interconnect proporciona principalmente dos tipos de servicios:

1. Comunicación por teléfono fijo. El teléfono se puede conectar a varias líneas de manera simultánea.

2. Internet. La red se puede configurar a través de una línea telefónica (DSL, *línea de abonado digital*) o a través de un cable de fibra óptica.

Algunos otros servicios que ofrece la empresa incluyen:

- Seguridad en Internet: software antivirus (*ProtecciónDeDispositivo*) y un bloqueador de sitios web maliciosos (*SeguridadEnLínea*).
- Una línea de soporte técnico (*SoporteTécnico*).
- Almacenamiento de archivos en la nube y backup de datos (*BackupOnline*).
- Streaming de TV (*StreamingTV*) y directorio de películas (*StreamingPelículas*)

La clientela puede elegir entre un pago mensual o firmar un contrato de 1 o 2 años. Puede utilizar varios métodos de pago y recibir una factura electrónica después de una transacción.

### Descripción de los datos

Los datos consisten en archivos obtenidos de diferentes fuentes:

- `contract.csv` — información del contrato;
- `personal.csv` — datos personales del cliente;
- `internet.csv` — información sobre los servicios de Internet;
- `phone.csv` — información sobre los servicios telefónicos.

En cada archivo, la columna `customerID` (ID de cliente) contiene un código único asignado a cada cliente. La información del contrato es válida a partir del 1 de febrero de 2020.

### Pasos a seguir

Se realizo:

- Carga de datos
- Preprocesamiento de datos
- Análisis exploratorio de datos
- Entrenamiento y Evaluación del modelo: En este proyecto se implemento el modelo 'RandomForestClassifier'

### Resultados

Los resultados obtenidos fueron:

📊 **Classification Report**

| Métrica       | Clase 0 (No Churn) | Clase 1 (Churn) | Interpretación |
|---------------|--------------------|-----------------|----------------|
| **Precision** | 0.84               | 0.75            | - De los predichos como "No Churn", el 84% eran correctos.<br>- De los predichos como "Churn", el 75% realmente cancelaron. |
| **Recall**    | 0.79               | 0.81            | - Detectó el 79% de los clientes que NO cancelaron.<br>- Identificó el 81% de los clientes que SÍ cancelaron. |
| **F1-Score**  | 0.81               | 0.78            | Balance entre precisión y recall (ideal >0.8) |

🔹 **Accuracy**: 80% (bueno, pero no lo uses como métrica principal por el desbalance inicial).  
🔹 **Macro Avg**: Promedio no ponderado (importante si ambas clases son igualmente relevantes).


📈 **AUC-ROC: 0.8812**

- **Rango excelente:** 0.88 está muy por encima del mínimo objetivo de 0.85.

- **Interpretación:**

    ○ 1.0 = Predicción perfecta

    ○ 0.88 = Excelente capacidad para distinguir entre clientes que cancelarán o no.

    ○ 0.5 = Aleatorio

👉 **El modelo tiene un 88% de probabilidad de clasificar correctamente un par aleatorio (cliente que cancela vs uno que no).**


📌 **Matriz de Confusión**

|      | Predicción: 0 | Predicción: 1 | Total |
|---------------|--------------------|-----------------|----------------|
| **Realidad: 0** | 762              | 208           | 970     |
| **Realidad: 1**    | 147             | 629          | 776   |

- **Verdaderos Negativos (762):** Correctamente identificados como no churn.

- **Falsos Positivos (208):** Clientes leales marcados como riesgo (pueden recibir promociones innecesarias).

- **Falsos Negativos (147):** Clientes que cancelarán pero el modelo no detectó (los más críticos).

- **Verdaderos Positivos (629):** Correctamente identificados como churn.


📈 **Curva ROC (AUC = 0.88)**

🎯 **Interpretación de la Curva ROC**

- **Punto Óptimo**:  

    Se acerca al ideal (área bajo curva = 88%)


## 📌 Conclusiones Finales

A lo largo del análisis realizado para la empresa Interconnect, se identificaron factores clave que influyen en la cancelación de clientes (churn). Entre los hallazgos más relevantes se destacan los siguientes:

- Los clientes con contratos mes a mes son significativamente más propensos a cancelar el servicio, mientras que aquellos con contratos de uno o dos años muestran una mayor retención. Esto sugiere que incentivar contratos a largo plazo puede reducir la tasa de churn.

- El método de pago también se relaciona con la cancelación: los usuarios que pagan mediante cheque electrónico cancelan con más frecuencia que aquellos que utilizan métodos automáticos como tarjeta de crédito o transferencia bancaria.

- Los clientes que no cuentan con servicios de seguridad online ni con soporte técnico tienden a cancelar más. Esto indica que los servicios adicionales tienen un impacto positivo en la fidelización.

- Curiosamente, el servicio de internet por fibra óptica, aunque más moderno, presenta una tasa de cancelación más alta que el DSL. Esto podría estar relacionado con expectativas no cumplidas o problemas en el servicio.

En conjunto, estos resultados ofrecen una base sólida para que el equipo de marketing de Interconnect diseñe estrategias de retención más efectivas, como ofrecer promociones a quienes usan pago electrónico, fomentar contratos de largo plazo, o incluir servicios de soporte técnico y seguridad online en los paquetes básicos.
