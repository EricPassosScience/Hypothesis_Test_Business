# La Prueba de Hipótesis como Herramienta Empresarial

Considerando su importancia, agrego nuevamente en este repositorio una nueva prueba de hipótesis.

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

# Iniciar trabajos en RStudio
***Configurar el directorio de trabajo***
- setwd("/Users/EricHenriquedaSilvaP/Desktop/TestesH/Arquivos")
- getwd()

***Paquetes Requeridos***
- install.packages("readxl")
- install.packages("e1071")
- library(readxl)
- library(e1071)

***Cargando y viendo el conjunto de datos***
- dados <- read_excel("balon_futbol.xlsx")
- View(dados)
- dim(dados)
- str(dados)

![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/74d6e476-a154-408c-8389-3078df1bd9a5)

***Comprobando valores faltantes***
- colSums(is.na(dados))

***Calculando las estadisticas***
- summary(dados)

![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/d0cd4a48-55c4-45ab-acc5-c201be245f3b)

***Vector con el nombre de estadísticas***
- nomes_stats <- c("Média", "Desvio Padrão", "Variância", "Tipo de Bola")

***Calcular estadísticas para la bola recubierta actual***
- dados_stats_atual <- c(round(mean(dados$Atual), digits = 2),
                       round(sd(dados$Atual), digits = 2), 
                       round(var(dados$Atual), digits = 2),
                       "Bola com Revestimento Atual")

***Calcular estadísticas para la bola recién recubierta***
- dados_stats_novo <- c(round(mean(dados$Novo), digits = 2), 
                      round(sd(dados$Novo), digits = 2), 
                      round(var(dados$Novo), digits = 2),
                      "Bola com Revestimento Novo")

***Combinar resultados para comparar***
- dados_stats_combined <- rbind(nomes_stats, dados_stats_atual, dados_stats_novo)
- View(dados_stats_combined)

![imagem](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/b2f9726f-bf7b-4f9d-817f-b7ea29ee99e9)

## Análisis univariado
***Range1***
- range_atual <- max(dados$Atual) - min(dados$Atual)
- range_atual

***Range2***
- range_novo <- max(dados$Novo) - min(dados$Novo)
- range_novo

***Rango intercuartil***
- summary(dados)
- IQR_atual <- IQR(dados$Atual)
- IQR_atual

- IQR_novo <- IQR(dados$Novo)
- IQR_novo

***Algunas Observaciones***

El rango intercuartil de ambas variables equivale aproximadamente a 12, es decir, no existe diferencia entre los valores del primer al tercer cuartil (valores alrededor de la media)

Del promedio se puede decir que las pelotas del modelo de recubrimiento actual recorren una distancia mayor que las pelotas del nuevo modelo, pero la desviación estándar es muy similar. Por tanto, podemos decir que no existe ninguna diferencia (significativa) entre los dos modelos de revestimientos de pelotas.

***Representación Gráfica***
