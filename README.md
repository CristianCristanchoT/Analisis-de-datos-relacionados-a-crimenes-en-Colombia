# Gestión  de datos
# Taller 1 

### Presentado por:
- Nikolas Rodriguez
- Angie Zapata
- Cristian Cristancho


### 1. Seleccione al menos 4 conjuntos de datos y realice un perfilamiento de cada uno. Describa los hallazgos encontrados en cada conjunto de datos. No olvide mencionar su estructura y aspectos relevantes de calidad como campos nulos, departamentos mal escritos, formatos de fechas incorrectos, entre otros. Si no evidencia ningún problema de calidad de datos, también menciónelo.


"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."


### 2. Responda las siguientes preguntas para cada uno de los conjuntos de datos seleccionados:

Debido a la necesidad de generar análisis de frecuencias de variables categoricas, se genera una función que permite recibir el dataframe a analizar y posteriormente obtener los últimos 5 años del dataframe y encontrar los 3 valores con más registros: 

![Test Image 2](/img/Funcion.png)

##### 2.1. ¿Cuáles han sido los departamentos (TOP 3) más afectados en términos de cantidad de delitos cometidos en los últimos 5 años?

Utilizando la función descrita en el punto anterior se logra obtener la siguiente distribución: 

![Test Image 2](/img/top3.png)

##### 2.2. Para los casos en los que aplique, ¿cuál ha sido el arma o medio más común para cometer el delito?

Utilizando la función descrita en el punto anterior se logra obtener la siguiente distribución: 

![Test Image 2](/img/top3armas.png)

##### 2.3. Para los casos en los que aplique, ¿cómo ha sido la proporción de géneros y grupos etarios que han estado involucrados en este tipo de delito? ¿Han variado con el paso de los años?

Utilizando la función descrita en el punto anterior se logra obtener la siguiente distribución: 

* Genero:

![Test Image 2](/img/ProporciónGenero.png)

*Rango étareo

![Test Image 2](/img/ProporcionEtarea.png)

Revisando la variación de estos delitos a lo largo de los años se logra evidenciar los siguientes patrones: 

*. Para maltrato intrafamiliar se logra ver un incremento en el año 2020 debido a la pandemia y un decaimiento en los casos de homicidios debido por la misma razón.

![Test Image 2](/img/Pandemia.png)


##### 2.4. ¿Se evidencia alguna tendencia para cometer dicho delito en algún mes particular del año?

*. Para los tres casos análizados se logra evidenciar un pico o cresta en la serie temporal en los meses de diciembre

![Test Image 2](/img/Diciembre.png)

##### 2.5. Para los casos en los que se disponga del detalle del delito o de una descripción, como por ejemplo en delitos sexuales y secuestro, ¿cuáles 

[['ARTÍCULO 209. ACTOS SEXUALES CON MENOR DE 14 AÑOS',
  'ARTÍCULO 208. ACCESO CARNAL ABUSIVO CON MENOR DE 14 AÑOS',
  'ARTÍCULO 205. ACCESO CARNAL VIOLENTO']]
  
  ![Test Image 2](/img/delito.png)

### 3. A partir de alguno de los conjuntos de datos seleccionados, visualice una serie de tiempo por año y mes que permita comparar la cantidad de delitos cometidos para los departamentos con mayor ocurrencia durante los últimos 5 años. Para que los resultados entre departamentos sean comparables, es importante que normalice las cantidades obtenidas por cantidad de habitantes. En este archivo puede encontrar la población por departamento para el año 2018. Asuma que la población no ha cambiado con el paso de los años.

Para dar solución a este punto es necesario realizar un merge entre los datasets trabajados hasta el momento y el conjunto de datos con la información por municipio.

Se generarón dos análisis, el primero es la cantidad de delitos cometidos en cada uno de los departamentos sin normalizar:

  ![Test Image 2](/img/Serie1.png)
  
Para el segundo análisis se genera una normalización correspondiente a la cantidad de delitos sobre la cantidad de población por departamento: 


  ![Test Image 2](/img/Serie2.png)


### 4. A partir de los conjuntos de datos seleccionados, construya un único dataset que integre la totalidad de los delitos ocurridos por departamento y municipio. Muestre los valores normalizados por cantidad de habitantes realizando un proceso similar al del punto anterior. Utilice la proyección para el año en curso. Considere solamente los municipios con más de 1 millón de habitantes.

"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."

### 5. Grabe un video de máximo 5 minutos en donde muestre el proceso realizado y los hallazgos más importantes de los diferentes análisis. Suba el video a YouTube. Todos los integrantes del equipo deben participar en el video.

[![IMAGE ALT TEXT](http://img.youtube.com/vi/mCdA4bJAGGk/0.jpg)](http://www.youtube.com/watch?v=mCdA4bJAGGk "Video de presentacion")



