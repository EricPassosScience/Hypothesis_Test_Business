# La Prueba de Hipótesis como Herramienta Empresarial

Considerando su importancia, agrego nuevamente en este repositorio una nueva prueba de hipótesis.

**********************
# Prueba de Hipótesis
Las pruebas de hipótesis desempeñan un papel clave tanto en el ámbito estadístico como empresarial, proporcionando un enfoque sistemático para evaluar suposiciones y tomar decisiones informadas. Este método implica formular una hipótesis sobre una situación o fenómeno, recopilar datos relevantes, aplicar una prueba estadística adecuada y, en función de los resultados, aceptar o rechazar la hipótesis formulada.

En el contexto empresarial, las pruebas de hipótesis son de gran importancia. Las empresas a menudo enfrentan dilemas e incertidumbres que requieren un análisis riguroso para guiar sus estrategias y decisiones. Aquí hay algunos puntos clave que resaltan la relevancia de estas pruebas:

- **Validación de Supuestos**: Las empresas operan con base en supuestos y conjeturas sobre el mercado, comportamiento del consumidor, efectividad de las estrategias de marketing, entre otros. Las pruebas de hipótesis permiten someter estos supuestos a pruebas empíricas, reduciendo el margen de error en las decisiones.
- **Tomar decisiones informadas**: las decisiones comerciales pueden tener implicaciones importantes en términos de recursos, tiempo y dinero. Al aplicar Pruebas de Hipótesis, las empresas pueden evaluar diferentes cursos de acción basados ​​en evidencia estadística sólida, minimizando los riesgos asociados a la toma de decisiones.
- **Evaluación de estrategias**: ya sea lanzando un nuevo producto, ajustando precios o expandiéndose a nuevos mercados, las estrategias comerciales a menudo implican decisiones complejas. Las pruebas de hipótesis le permiten comparar objetivamente diferentes enfoques, identificando aquel que tiene más probabilidades de lograr los objetivos deseados.
- **Monitoreo del desempeño**: las empresas monitorean constantemente su desempeño y se adaptan a los cambios en el entorno empresarial. Las pruebas de hipótesis permiten a las empresas determinar si los cambios observados en los datos son estadísticamente significativos o pueden atribuirse al azar.
- **Comprender el mercado y los clientes: comprender el mercado y las preferencias de los clientes es fundamental. Las pruebas de hipótesis se pueden utilizar para analizar datos de investigación de mercado, sentimiento del consumidor y otros datos relevantes para obtener información sobre el comportamiento del cliente.
- **Apoyar la innovación**: al desarrollar nuevos productos o servicios, las empresas deben evaluar si existe una demanda real y sostenible. Las pruebas de hipótesis ayudan a comprobar si las innovaciones propuestas tienen un impacto significativo antes de invertir recursos sustanciales en ellas.
- **Evidencia científica**: Para las empresas que buscan asociaciones, inversores o financiación, la capacidad de respaldar sus afirmaciones con datos estadísticos fiables puede aumentar la credibilidad y la confianza de las partes interesadas.

*********************************************
# Pruebas de hipótesis en la industria del deporte
![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/f86b1c35-d323-4131-b38c-d29139381275)

La empresa ficticia boomBola Inc es un importante fabricante de equipamiento deportivo. Cree que puede aumentar su cuota de mercado introduciendo un nuevo balón de fútbol más duradero y con un revestimiento resistente a cortes y deformaciones, capaz de cubrir una mayor distancia.

Las pruebas con el nuevo recubrimiento en la pelota han sido prometedoras y ahora quieren ver el efecto del nuevo recubrimiento en la distancia total recorrida por la pelota cuando se patea.

El objetivo de este proyecto es analizar el conjunto de datos utilizando R y extraer información valiosa con el objetivo principal de estudiar el efecto del nuevo recubrimiento en la distancia total recorrida.
El conjunto de datos (ficticios) proporcionado por la empresa tiene dos columnas:
- variable_1: distancia total en metros recorrida por el balón con el revestimiento actual al ser pateado;
- variable_2: distancia total en metros recorrida por el balón con el nuevo revestimiento al ser pateado.

Cuando aplicamos una prueba de hipótesis, definimos dos hipótesis, llamada hipótesis nula, que es la que queremos probar, y la hipótesis alternativa, la opción contraria a lo que queremos probar.

La definición de hipótesis la realiza el científico de datos. Para este caso, podemos definir las hipótesis de la siguiente manera:
- **Hipótesis nula (H0)** - No existe diferencia significativa entre la distancia recorrida por balones de fútbol con revestimiento actual y nuevo
- **Hipótesis alternativa (H1)** - Existe una diferencia significativa entre las distancias recorridas por balones de fútbol con revestimientos actuales y nuevos.

Tenga en cuenta que en este caso solo estamos probando en H1 si la distancia recorrida por la pelota es diferente. A esto se le llama prueba de dos colas. Podríamos probar si la distancia recorrida es mayor que un valor o menor que un valor, en cuyo caso sería una prueba de una cola.
![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/aad0c34c-5c66-4284-aa18-fab7d64c9b37)

*******************************
# Iniciar trabajos en RStudio
***Configurar el directorio de trabajo***
- setwd("/Users/EricHenriquedaSilvaP/Desktop/TestesH/Arquivos")
- getwd()

***********************

***Paquetes Requeridos***
- install.packages("readxl")
- install.packages("e1071")
- library(readxl)
- library(e1071)

*************************************

***Cargando y viendo el conjunto de datos***
- dados <- read_excel("balon_futbol.xlsx")
- View(dados)
- dim(dados)
- str(dados)

![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/74d6e476-a154-408c-8389-3078df1bd9a5)

*****************************************

***Comprobando valores faltantes***
- colSums(is.na(dados))

****************************************
***Calculando las estadisticas***
- summary(dados)

![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/d0cd4a48-55c4-45ab-acc5-c201be245f3b)

********************************************
***Vector con el nombre de estadísticas***
- nomes_stats <- c("Média", "Desvio Padrão", "Variância", "Tipo de Bola")

******************************************
***Calcular estadísticas para la bola recubierta actual***
- dados_stats_atual <- c(round(mean(dados$Atual), digits = 2),
                       round(sd(dados$Atual), digits = 2), 
                       round(var(dados$Atual), digits = 2),
                       "Bola com Revestimento Atual")

*************************************************
***Calcular estadísticas para la bola recién recubierta***
- dados_stats_novo <- c(round(mean(dados$Novo), digits = 2), 
                      round(sd(dados$Novo), digits = 2), 
                      round(var(dados$Novo), digits = 2),
                      "Bola com Revestimento Novo")

*****************************************************
***Combinar resultados para comparar***
- dados_stats_combined <- rbind(nomes_stats, dados_stats_atual, dados_stats_novo)
- View(dados_stats_combined)

![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/b2f9726f-bf7b-4f9d-817f-b7ea29ee99e9)

******************************************************
## Análisis univariado
***Range1***
- range_atual <- max(dados$Atual) - min(dados$Atual)
- range_atual

*************************************************
***Range2***
- range_novo <- max(dados$Novo) - min(dados$Novo)
- range_novo
***************************************
***Intervalo Intercuartil***
- summary(dados)
- IQR_atual <- IQR(dados$Atual)
- IQR_atual

- IQR_novo <- IQR(dados$Novo)
- IQR_novo
******************************************
***Algunas Observaciones***

El Intervalo intercuartil de ambas variables equivale aproximadamente a 12, es decir, no existe diferencia entre los valores del primer al tercer cuartil (valores alrededor de la media)

Del promedio se puede decir que las pelotas del modelo de recubrimiento actual recorren una distancia mayor que las pelotas del nuevo modelo, pero la desviación estándar es muy similar. Por tanto, podemos decir que no existe ninguna diferencia (significativa) entre los dos modelos de revestimientos de pelotas.

 ****************************
***Algunas observaciones***

La distribución normal es la distribución más fácil con la que trabajar para comprender las estadísticas. Las distribuciones en la vida real suelen estar sesgadas. Demasiada asimetría y demasiadas técnicas estadísticas no funcionan. Como resultado, se utilizan técnicas matemáticas avanzadas, incluidos logaritmos y técnicas de regresión cuantil.

Podemos ver algunos métodos para diferentes distribuciones en la siguiente imagen:

![imagem_](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/16e6bd17-deaa-4d35-bb53-06ffd4607d68)
Source: XKCD 2048 as amended by Anton Antonov for a 2019 talk at an R-user meeting in Boston.

Referencia de imagen -> http://www.econ.uiuc.edu/~roger/research/rq/rq.html

*****************************
# REPRESENTACIÓN GRÁFICA
*****************************
***Ajusta el área de la trama***
- par(mfrow = c(2,2))

***HISTOGRAMA***
## Histograma
Un histograma está sesgado hacia la derecha si el pico del histograma se desplaza hacia la izquierda. Por tanto, la cola del histograma tiene pendiente derecha positiva. El razonamiento inverso es el mismo.

- hist(dados$Atual, 
     main = "Distancia - Pelota con revestimiento actual", 
     xlab = "Distância (metros)", 
     ylab = "Numero de Pelotas", 
     col = "Blue")

- hist(dados$Novo, 
     main = "Distancia - Pelota con revestimiento actual", 
     xlab = "Distancia (metros)", 
     ylab = "Número de Pelotas", 
     col = "Green")

![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/0a1def59-eee3-4f94-8f24-236c62c75821)

*****************************
## BOXPLOT
- boxplot(dados$Atual, 
        main = "Distancia - Pelota con revestimiento actual", 
        xlab = "Distancia (metros)", 
        ylab = "Número de Pelotas", 
        col = "Blue", 
        horizontal = TRUE)

- boxplot(dados$Novo, 
        main = "Distancia - Pelota con revestimiento nuevo", 
        xlab = "Distancia (metros)", 
        ylab = "Número de Pelotas", 
        col = "Green", 
        horizontal = TRUE)

![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/7ab702aa-9601-4f29-bc9f-a040b6e47e52)
*************************************
Boxplot asimétrico izquierdo:
Si la mayoría de las observaciones están en el extremo superior de la escala, el diagrama de caja estará sesgado hacia la izquierda. En consecuencia, el "bigote" izquierdo es más largo que el "bigote" derecho. Como resultado, la media es menor que la mediana.

Boxplot asimétrico a la derecha:
Si un diagrama de caja está sesgado hacia la derecha, el cuadro se desplazará hacia la izquierda y el "bigotes" derecho se hará más largo. Como resultado, la media es mayor que la mediana.

Por lo tanto, la variable revestida de corriente está sesgada hacia la derecha, ya que la mayoría de los datos se encuentran a la derecha del "pico". La media es mayor que la mediana.

La nueva variable de recubrimiento también está sesgada (asimétrica) hacia la derecha, ya que la mayoría de los datos se encuentran a la derecha del gráfico. La media es mayor que la mediana.
********************************************
***ASÍMETRIA***

Si una cola es más larga que la otra, la distribución es asimétrica o sesgada. Estas distribuciones a veces se denominan distribuciones asimétricas porque no muestran ningún tipo de simetría. La simetría significa que la mitad de la distribución es una imagen especular de la otra mitad. Por ejemplo, la distribución normal es una distribución simétrica sin pendiente. Las colas son exactamente iguales.

Una distribución sesgada hacia la izquierda tiene una cola izquierda larga. Las distribuciones sesgadas hacia la izquierda también se denominan distribuciones sesgadas negativamente. Esto se debe a que hay una cola larga en la dirección negativa en la recta numérica. La media está a la izquierda del pico.

Una distribución sesgada a la derecha tiene una cola derecha larga. Las distribuciones de pendiente derecha también se denominan distribuciones de pendiente positiva. Esto se debe a que hay una cola larga en dirección positiva en la recta numérica. La media está a la derecha del pico.

En una distribución normal, la media y la mediana son el mismo número, mientras que la media y la mediana en una distribución asimétrica se convierten en números diferentes. Luego podemos calcular el coeficiente de asimetría.

Si la asimetría es menor que -1 o mayor que 1, la distribución está muy asimétrica. Si la asimetría está entre -1 y -0,5 o entre 0,5 y 1, la distribución está moderadamente asimétrica (asimétrica). Si la asimetría está entre -0,5 y 0,5, la distribución es aproximadamente simétrica.

Una medida positiva indicaría que la media de los valores de los datos es mayor que la mediana y la distribución de los datos está sesgada hacia la derecha.

Una medida negativa indica que la media de los valores de los datos es menor que la mediana y la distribución de los datos está sesgada hacia la izquierda.
****************************************
skewness(dados$Atual)
- 0.2835894

summary(dados$Atual)

![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/13084658-6419-43f7-8b1a-3f85f94c1051)

skewness(dados$Novo)
- 0.2221244

summary(dados$Novo)

![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/09a71d47-e06a-40f0-8545-f8f9f924470e)
*****************************
***CURTOSIS***

La curtosis informa sobre la altura y la nitidez del pico central en relación con una curva de campana estándar. La distribución normal tiene una curtosis igual a cero.

Una curtosis negativa significa que su distribución es más aplanada que una curva normal con la misma media y desviación estándar. El razonamiento inverso es el mismo.
********************************
- kurtosis(dados$Atual)
- kurtosis(dados$Novo)
 
![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/3de482ed-b56f-4e18-bbd2-af634984947b)

***********************************
Si estás realizando una prueba estadística paramétrica en tus datos (por ejemplo, un ANOVA), el uso de datos altamente sesgados hacia la derecha o hacia la izquierda puede llevar a resultados engañosos. Por lo tanto, si deseas realizar una prueba con este tipo de datos, realiza una transformación logarítmica y luego lleva a cabo la prueba en los números transformados.
**********************************
***TEST DE NORMALIDAD - PRUEBA DE SHAPIRO***
- Hipótesis Nula (H0): Los datos siguen una distribución normal.
- Hipótesis Alternativa (H1): Los datos no siguen una distribución normal.
**********************************
Si el valor p es mayor que 0.05, no rechazamos la hipótesis nula y podemos asumir que los datos siguen una distribución normal.

Si el valor p es menor que 0.05, rechazamos la hipótesis nula y no podemos asumir que los datos siguen una distribución normal.
********************************
- ?shapiro.test
- shapiro.test(dados$Atual)
- shapiro.test(dados$Novo)

![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/0bc57d8a-788c-443e-be68-7748b51aebb8)

***CONCLUSIÓN DEL ANÁLISIS UNIVARIADO:***

Del diagrama de caja y de otros análisis se puede decir que no hay discrepancias. La media del modelo de recubrimiento actual es 270,3 y la media del nuevo modelo es 267,5 y la desviación estándar del actual es 8,7529 y la desviación estándar del nuevo es 9,8969. No parece haber una diferencia significativa.
************************************
***ANÁLISIS BIVARIADO***
***Ajusta el área de la trama***
- par(mfrow = c(1,1))
***Scatter Plot***
- plot(dados$Atual, dados$Novo)

![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/c8f227cb-fe38-4726-adb0-413db3763887)

***Correlación***
- cor(dados$Atual, dados$Novo)

[1] -0.08272974
******************************
## Prueba de Hipótesis:
La prueba de hipótesis es una forma de inferencia estadística que utiliza datos de una muestra para sacar conclusiones sobre un parámetro poblacional o una distribución de probabilidad poblacional.

Primero, se hace una suposición tentativa sobre el parámetro o distribución. Esta suposición se denomina hipótesis nula y se denota por H0. Una hipótesis alternativa (denotada como H1) es lo opuesto a lo que se afirma en la hipótesis nula. El procedimiento de prueba de hipótesis implica el uso de datos de muestra para determinar si H0 puede rechazarse o no.

Si se rechaza H0, la conclusión estadística es que la hipótesis alternativa H1 es verdadera.

***FORMULACIÓN DE LA HIPÓTESIS:***

Hipótesis nula (H0): no existe una diferencia significativa entre la distancia recorrida por balones de fútbol con revestimiento actual y nuevo.
H0: muCurrent - muNew igual a 0 (cero)

Hipótesis alternativa (H1): existe una diferencia significativa entre la distancia recorrida por balones de fútbol con revestimientos actuales y nuevos.
H1: muCurrent - muNew diferente de 0 (cero)

La condición preliminar para aplicar la prueba t es la existencia de una distribución normal de datos en ambos grupos de datos.

Sin embargo, ¡hay un punto muerto! Hay tres tipos de pruebas t:
- prueba t de una muestra
- prueba t de muestras independientes
- prueba t de muestras relacionadas (pareadas)

Utilizamos la prueba t de una muestra para comparar los valores de las variables con la media conocida de una población.

Para realizar las pruebas de igualdad de varianzas y las pruebas de medias necesitamos que las dos poblaciones sean independientes. Esta es una prueba de muestras independientes. Por lo tanto emparejado = F.
***********************************
- ?t.test
- teste_hipo <- t.test(dados$Atual, dados$Novo, paired = F, conf.level = 0.95, alternative = "t") 
- teste_hipo

![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/3e7aa3b7-5fb6-4373-8e6f-9239498e1bdc)

La prueba t pareada es útil para analizar el mismo conjunto de elementos que se midieron en dos condiciones diferentes, diferencias en las mediciones tomadas en el mismo sujeto antes y después de un tratamiento, o diferencias entre dos tratamientos administrados al mismo sujeto.

En este caso, estamos utilizando la prueba t para muestras independientes.
***************************************
***INTERPRETACIÓN DE NUESTRO RESULTADO:***

No pudimos rechazar la hipótesis nula, ya que el valor p es mayor que el umbral de 0,05. Es decir, existe una alta probabilidad de que no exista una diferencia significativa entre los tipos de cobertura de los balones de fútbol.

Valor p bajo: evidencia empírica sólida contra H0.

Valor p alto: poca o ninguna evidencia empírica contra H0.
******************************
***Determinación de la fuerza de la prueba y el tamaño óptimo de la muestra***
*******************************
***Diferencia de Medias***
- delta_mean <- mean(dados$Atual) - mean(dados$Novo)
- delta_mena

[1] 2.775
**********************************
***Desviación estándar de la diferencia entre los datos:***
- delta_desvio <- sd(dados$Atual - dados$Novo)
- delta_desvio
  
[1] 13.74397

***Size Effect:***
- size_effect = delta_mean/delta_desvio
- size_effect

[1] 0.2019067
*****************************
***POWER TEST - PRUEBA DE FUERZA***
- install.packages("pwr")
- library(pwr)
- dim(dados): [1] 40  2
- power_teste <- pwr.t.test(n = 40, d = size_effect, sig.level = 0.05, alternative = "t")
- power_teste:

![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/e2ef958c-0d10-48a6-a462-1a1ed36c8fee)
***************************
***Tamaño de Muestra Ideal***
- tamanho_amostra <- pwr.t.test(power = .95, d = 0.5, type = "t", alternative = "t", sig.level = .05)
- tamanho_amostra:

![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/e060bc79-d691-4e63-a570-1b9d5df0b86e)
********************************
# Conclusiones y Recomendaciones 
***Resultado de la prueba de hipótesis:***
- el valor p es 0,188 y por lo tanto no podemos rechazar la hipótesis nula. Por tanto, podemos decir que no existe diferencia entre la distancia recorrida por el balón con la cobertura actual y la nueva;
- debe haber algún factor distinto del revestimiento que afecte la distancia recorrida por el balón de fútbol;
- la empresa no debería introducir el nuevo modelo en el mercado.
*****************************
***Intervalos de confianza***:
- Intervalo de confianza del 95% para el modelo actual [273.0743, 267.4757]
- Intervalo de confianza del 95% para el nuevo modelo [270,6652, 264,3348]

Por lo tanto, la media poblacional respectiva debe estar dentro de este rango para obtener resultados consistentes.
***********************************
***Fuerza de la prueba y tamaño de la muestra:***
- la intensidad de la prueba es 0,144, que es baja;
- tamaño de la muestra: la prueba debe realizarse con un tamaño de muestra mayor, al menos 105 registros;
- Siempre es mejor tener un tamaño de muestra mayor para obtener mejores resultados, pero también se deben tener en cuenta otros factores como el coste, la viabilidad y el tiempo.
**************************************
***RECOMENDACIONES:***
- estadísticamente, no hay diferencia significativa entre la distancia recorrida entre balones de fútbol con revestimiento actual y nuevo;
- la empresa debe continuar su estudio y considerar otros factores que afectan la distancia, como el tamaño y peso de la pelota, su material de fabricación, relleno, tecnología y número de segmentos;
- también debería considerar la tecnología predominante en el sector y los productos lanzados por sus competidores;
- a partir de ahora, para aumentar su cuota de mercado, la empresa deberá centrarse en otras áreas como marketing, estrategias, ventas y seguir trabajando en investigación y desarrollo.
