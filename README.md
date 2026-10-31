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


**VISUALIZACIONES GRAFICAS**


<img width="549" height="389" alt="image" src="https://github.com/user-attachments/assets/61233259-614c-4288-8c5d-b9d439f64ff1" />


En el grafico de barras agrupados visualizamos cuantos usuarios absolutos se conviertieron a clientes y en que tipo de Fuuente de trafico, y cuantos no se convirtieron.

Predominio en Volumen (Organic): El tráfico Organic representa la mayor cantidad absoluta de usuarios en la plataforma. Registra la mayor barra de no convertidos (15,500) y el mayor volumen absoluto de convertidos (2,480).

Canales Menores (Email y Referral): Email y Referral registran los menores volúmenes absolutos de tráfico. Aunque Email tiene un volumen total menor que Ads y Organic, mantiene un número considerable de usuarios convertidos en relación a su tamaño total.


<img width="557" height="332" alt="image" src="https://github.com/user-attachments/assets/8d8705ef-1802-4fff-a640-fc7c3776223b" />


**Liderazgo en conversión:** Email se visualiza como el canal más efectivo con una tasa de conversión del 14.99%, seguido de cerca por Ads con un 14.74%.

**Canales con menor rendimiento:** Referral alcanza un 13.88% y Organic se sitúa en el extremo inferior con un 13.79%.


<img width="556" height="391" alt="image" src="https://github.com/user-attachments/assets/546caac8-33c9-4404-a9c9-16b52ddd888b" />

El grafico nos muestra cuantos usuarios se convirtieron a clientes por tipo y cuando no se convirtieron y de que tipo.

**Dominio del Tráfico por Usuarios Nuevos:** La mayor concentración de visitas proviene de usuarios Nuevos, registrando algo más de 22,000 usuarios no convertidos y cerca de 3,700 convertidos.

**Volumen de Usuarios Recurrentes:** El segmento de usuarios Recurrentes maneja una escala menor, alcanzando aproximadamente 12,000 no convertidos y cerca de 2,000 convertidos.


🌟 **Insight Ejecutivo basado en el Experimento A/B**

**Gasto promedio por usuario que convirtió:**

*La Página B* optimiza (o mantiene) la conversión, eleva de manera drástica el ticket promedio / gasto por usuario.
El gasto promedio por usuario entre la Página A y la Página B no es igual. El signo negativo en el estadístico (asumiendo la resta A−B) indica que la Página B genera un gasto significativamente mayor que la Página A.

*Interpretación:*

    Existe evidencia abrumadora para concluir que el gasto promedio por usuario entre la Página A y la Página B no es igual

**Tasa de conversión:** 
- La Página B supera estadísticamente a la Página A en las dos métricas clave de negocio: tasa de conversión (p=4.33×10 −22) y gasto promedio por usuario (p=3.63×10 −21)
  
- No existe ningún trade-off (ganar conversión a costa de vender más barato).
  
- *Interpretación:*

    La versión B demostró ser superior porque logró que un porcentaje mayor de visitantes comprara y que cada uno de ellos gastara más dinero en su compra.


  **Segmentación por fuente de tráfico**

  Aporte al Volumen General: Organic: motor principal que nutre el total absoluto de ventas (2,480 conversiones)
  
- *Interpretación:*
 
    El valor estadístico indica Diferencia moderada entre lo observado y lo esperado 8.662

    Ese 8.662 es la prueba matemática de que el tráfico no se comporta de manera homogénea. Confirma que las variaciones en las tasas de conversión (14.99% en Email vs. 13.79% en Organic) no son ruido aleatorio, sino una diferencia real en el comportamiento de compra según el canal de origen


  **Segmentación por tipo de usuario**

Al evaluar si un perfil muestra mayor probabilidad de conversión, los datos concluyen que ningún grupo supera al otro. La tasa de conversión es idéntica (≈14.26%) tanto para usuarios de primera visita como para usuarios recurrentes.


**Interpretación:**

 El hecho de que un usuario haya visitado la plataforma anteriormente no incrementa ni disminuye su propensión a completar una compra en la sesión actual. La fricción o motivación de compra afecta por igual a ambos segmentos.








   

