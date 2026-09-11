# NovaRetail+: qué comportamientos se asocian con el ingreso del cliente

## Desafío
NovaRetail+, una plataforma de comercio electrónico en Latinoamérica con millones de 
usuarios, necesitaba que el equipo de Crecimiento y Retención entendiera qué factores 
del comportamiento del cliente están más fuertemente asociados con el ingreso anual 
que genera, sin caer en interpretaciones causales que no estuvieran respaldadas por 
los datos.

En resumen, este proyecto es descubrir qué comportamientos hacen que un cliente de 
NovaRetail+ genere más ingreso, sin caer en la trampa de confundir que dos cosas se 
muevan juntas con que una cause la otra.

## Datos
Dataset de comportamiento de clientes de NovaRetail+ durante 2024, con 15,000 
registros y 12 columnas: variables numéricas (edad, nivel de ingreso, visitas al mes, 
compras al mes, gasto en publicidad dirigida, satisfacción, ingreso anual), binarias 
(si es miembro premium, si abandonó la plataforma) y categóricas (tipo de dispositivo, 
región).

## Proceso
- Carga y exploración inicial: revisión de tipos de dato, variables numéricas, 
  binarias y categóricas
- Documentación de supuestos: qué coeficiente de correlación usar según el tipo de 
  variable (Pearson para relaciones lineales, Spearman para relaciones monótonas, 
  punto biserial para numérica vs binaria, V de Cramér para categórica vs categórica)
- Visualización de relaciones con heatmap general y scatterplots, tanto generales 
  como para los pares de variables más relevantes
- Cálculo de los coeficientes correspondientes como evidencia numérica de cada patrón 
  observado visualmente
- Interpretación responsable de cada hallazgo, documentando evidencia visual, 
  evidencia numérica, qué se puede interpretar, qué no se puede afirmar (para no 
  caer en causalidad) y la implicación de negocio

Lo más particular de este proyecto fue aprender a identificar qué correlaciones, 
aunque muy altas, no valía la pena explorar a fondo porque eran resultados 
esperables, como que más compras generen más ingresos. En vez de eso, la atención se 
centró en relaciones menos evidentes que sí aportaban valor analítico. También fue 
la primera vez que se aplicaron varios tipos de correlación en un mismo análisis, y 
entender que cada uno está diseñado para un tipo de relación distinto fue clave 
para elegir bien la herramienta según cada par de variables.

## Resultado
- Las visitas mensuales se asocian de forma moderada-débil con el ingreso anual 
  (Pearson 0.3371, Spearman 0.3210)
- El gasto en publicidad dirigida está moderadamente asociado con más visitas 
  mensuales (Pearson 0.5789, Spearman 0.5593)
- Ser miembro premium se relaciona con menor abandono de la plataforma (punto 
  biserial -0.1205)
- No hay asociación relevante entre el tipo de dispositivo y la región del cliente 
  (V de Cramér 0.0124)

Es importante tener en cuenta que estas son asociaciones, no relaciones de causa y 
efecto: por ejemplo, no se puede afirmar que visitar más la plataforma cause un 
mayor ingreso, puede que los clientes con más disposición de compra sean 
naturalmente los que más visitan.

## Recomendaciones / Siguientes pasos
1. Probar segmentación adicional por membresía premium, región y tipo de 
   dispositivo, para ver si estas relaciones cambian según el grupo.
2. Analizar la relación entre satisfacción y abandono, para identificar clientes 
   con mayor riesgo de irse.
3. Calcular la tasa de conversión de visitas a compras por segmento, para explorar 
   qué factores se relacionan con tasas de conversión más altas.

## Visuales
<img width="1056" height="787" alt="Matriz de Correlación" src="https://github.com/user-attachments/assets/6112cc97-a492-45cf-8ff9-1cbd91390478" />
<img width="967" height="627" alt="Publicidad dirigida vs visitas mensuales" src="https://github.com/user-attachments/assets/f15995dd-85f7-4167-860b-8bdde3bc1edb" />

## Entregable
Notebook: https://github.com/sdachiardi/proyecto_novaretail/blob/main/analisis_novaretail.ipynb
