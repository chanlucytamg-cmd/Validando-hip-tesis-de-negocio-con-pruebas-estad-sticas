# Validando hipótesis de negocio con pruebas estadísticas de una empresa de ecommerce.
Se exploró, validó y analizó estadísticamente el experimento A/B para identificar diferencias significativas entre las páginas y traducir los resultados en recomendaciones para el negocio.


Se ejecutó un experimento A/B en la página de inicio (landing page), comparando dos versiones (A y B) con el objetivo de mejorar la tasa de conversión y el valor económico por usuario.

La empresa necesita una decisión basada en datos para definir qué versión implementar, considerando la tasa de conversión, el gasto promedio y el comportamiento por canal de tráfico y tipo de usuario.

**Dataset** 

/datasets/landing_experiment.csv: información de usuarios expuestos a las versiones A y B, incluyendo región, dispositivo, fuente de tráfico, tipo de usuario, conversión y gasto.

💡 **Preguntas del negocio**

¿Existe una diferencia significativa en el gasto promedio por usuario convertido entre ambas versiones?
<head></head>

¿Qué versión de la página (A o B) genera mayor tasa de conversión?
<head></head>

¿La conversión depende de la fuente de tráfico?
<head></head>

¿El tipo de usuario (nuevo o recurrente) influye en la conversión?
<head></head>

¿Qué hallazgos o insights permiten optimizar la estrategia de marketing y el diseño de la página de inicio (landing page)?


🔄 **Flujo general del proyecto**

1. Cargar y validar datos;	Confianza en la calidad del experimento
 <head></head>

2. Comparar gasto promedio (A vs. B);	Identificar qué página genera más valor
 <head></head>

3. Comparar tasa de conversión (A vs. B);	Identificar la página más efectiva
 <head></head>

4. Analizar tráfico y conversión;	Optimizar inversión en canales
 <head></head>

5. Analizar tipo de usuario y conversión;	Evaluar si segmentar usuarios
 <head></head>

6. Visualización;	Incluir gráficas que respalden las conclusiones
 <head></head>

7. Insight ejecutivo	Decisión clara para stakeholders

**Metodologia**

**Exploracion y validación de datos**
   - Dataset compuesto por 40,000 registros únicos de usuarios sin valores ausentes.
   - Distribución equitativa y balanceada de la muestra (50% en la variante A y 50% en la variante B).
   - Conversión de tipos de datos y análisis preliminar de variables categóricas (`traffic_source`, `user_type`, `dispositivo`, `region`).


**Comparación de Gasto Promedio (Ticket Promedio):**
   - Se aplicó la prueba de Levene para verificar homocedasticidad y una **prueba t de Student para muestras independientes** (`equal_var=False`).
   - **Resultado:** Se rechazó la hipótesis nula ($p < 0.05$). Los usuarios que convirtieron a través de la **Landing B** realizaron compras de mayor monto en comparación con la versión A.

**Análisis de la Tasa de Conversión:**
   - Se construyó una tabla de contingencia (2x2) y se aplicó la **prueba Chi-cuadrada de independencia**.
   - **Resultado:** Se rechazó la hipótesis nula con un valor $p$ altamente significativo ($\approx 4.33 \times 10^{-22}$). La versión B no solo incrementa el ticket promedio, sino que convierte a un porcentaje mayor de visitantes.


**Segmentación por Canales de Tráfico:**
   - Mediante pruebas Chi-cuadrada, se evaluó la relación entre la fuente de tráfico y la conversión ($p = 0.034$).
   - **Hallazgo:** Canales como **Email (14.99%)** y **Ads (14.74%)** presentan las tasas de conversión más eficientes por encima del promedio general.

 **Impacto del Tipo de Usuario:**
   - Se evaluó el comportamiento entre usuarios nuevos y recurrentes. No se encontró una asociación estadísticamente significativa ($p = 0.47$), lo que indica que el comportamiento de conversión es homogéneo independiente del historial de visitas previas.


💡 **Conclusiones y Recomendaciones de Negocio**

* **Implementación de la Versión B:** Se recomienda desplegar oficialmente la **Landing B** como la página de inicio predeterminada, ya que demuestra una superioridad estadística contundente tanto en la tasa de conversión como en el valor monetario generado por usuario.

  
* **Optimización de Canales de Adquisición:** Se aconseja reasignar y priorizar presupuesto hacia los canales de mayor rendimiento (*Email* y *Ads*), optimizando el Retorno de Inversión (ROI) en marketing.

**Tecnologías y Librerías Utilizadas**

* **Python**
* **Pandas / NumPy** (Manipulación y limpieza de datos)
* **SciPy** (`ttest_ind`, `levene`, `chi2_contingency` para pruebas de hipótesis estadísticas)
* **Matplotlib / Seaborn** (Visualización de datos y gráficos analíticos)




   

