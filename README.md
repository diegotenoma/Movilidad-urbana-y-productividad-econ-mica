# 🚦 Movilidad Urbana y Productividad Económica en LATAM

Análisis de la relación entre congestión vehicular y PIB per cápita en las 15 principales ciudades de América Latina, con el objetivo de identificar prioridades de inversión en infraestructura de transporte.

🎯 Pregunta de Negocio

¿La congestión vehicular y los tiempos de viaje actúan como frenos al crecimiento económico en las ciudades de LATAM? ¿Qué ciudades deberían ser prioritarias para inversión en infraestructura vial?

📂 Datasets Utilizados
Dataset	Fuente	Descripción
tomtom_traffic.csv	TomTom Traffic Index	Índices de tráfico en tiempo real: retrasos, atascos, velocidades y tiempos de viaje por ciudad
oecd_city_economy.csv	OECD Cities	Indicadores económicos por ciudad: PIB per cápita, desempleo, calidad del aire y población

Cobertura: 15 ciudades principales de LATAM — año 2024

🧩 Etapas del Análisis
1. Carga y Exploración Inicial
Carga de ambos datasets con pandas
Revisión de estructura: .info(), .head(), tipos de datos
2. Limpieza y Preparación de Datos
Estandarización de nombres de columnas a snake_case
Conversión de columnas de fecha a datetime con errors='coerce'
Limpieza de valores numéricos en eco:
Eliminación de separadores de miles, símbolos de % y comas en formato europeo
Conversión a float en city_gdp_capita, unemployment_pct y population_m
Creación de columna population en unidades absolutas (×1,000,000)
3. Filtrado y Agregación
Extracción de columna year desde fechas con .dt.year
Filtrado a registros del año 2024 con .copy() para preservar datasets originales
Cálculo de promedios de métricas de tráfico por city, country y year usando groupby + mean()
4. Integración de Datasets
Selección de columnas relevantes de cada dataset
JOIN tipo INNER sobre las claves city y year
Dataset resultante merged: tráfico + economía por ciudad
5. Visualización y Análisis
Boxplot de jams_delay para detectar outliers y comportamiento central
Histograma de city_gdp_capita para observar la distribución económica
Gráfico de barras doble eje para comparar retrasos de tráfico vs. PIB per cápita por ciudad
6. Exportación
Dataset final exportado como ladb_mobility_economy_2024_clean.csv
🔍 Hallazgos Principales

El análisis identificó tres grupos estratégicos de ciudades:

🔴 Prioridad 1 — Inversión Crítica (Cuello de Botella)

Ciudades con PIB relevante pero congestión extrema que probablemente ya está frenando su productividad potencial.

Ciudad de México — Caso más urgente del estudio. Retrasos masivos con alta productividad. Cada hora perdida en tráfico representa un impacto directo en horas-hombre y PIB.
Bogotá y São Paulo — Congestión muy alta en relación a ciudades con PIB similar. Su infraestructura actual ya fue superada por la demanda.
🟡 Prioridad 2 — Inversión Preventiva (Ciudades en Crecimiento)
Lima — Retrasos considerables con PIB en crecimiento. Si no se actúa ahora, el colapso vial es probable.
Santiago — PIB sólido y retrasos moderados. Invertir hoy evita llegar a niveles críticos de saturación.
🟢 Prioridad 3 — No Prioritarias (Gestionan bien la relación movilidad–economía)
Montevideo y Porto Alegre — PIB alto y congestión mínima. El retorno de inversión en infraestructura vial sería bajo comparado con las ciudades del grupo 1.
Curitiba — Alto PIB y baja congestión. Su modelo vial puede ser estudiado y replicado en ciudades con problemas de movilidad.
💡 Recomendación Ejecutiva

Ciudad de México, Bogotá y São Paulo son las ciudades donde la inversión en infraestructura de transporte tendría el mayor impacto económico medible. Reducir los tiempos de traslado en estas ciudades no solo mejora la calidad de vida, sino que libera capacidad productiva que actualmente se pierde en el tráfico.

🛠️ Tecnologías Utilizadas
Python 3
pandas
numpy
matplotlib
seaborn
Google Colab / Jupyter Notebook
▶️ Cómo Ejecutar el Proyecto
bash
# Clona el repositorio
git clone https://github.com/diegotenoma/<nombre-repo>.git
cd <nombre-repo>

# Instala dependencias
pip install pandas numpy matplotlib seaborn

# Abre el notebook
jupyter notebook S5_ladb_mobility_economy_project_clean.ipynb

Nota: Los archivos tomtom_traffic.csv y oecd_city_economy.csv deben estar disponibles en la ruta /datasets/ o ajusta las rutas de carga en el notebook según tu entorno.

👤 Autor

Diego Tenorio Martínez — Data Analyst
linkedin.com/in/tenoriodiego | github.com/diegotenoma
