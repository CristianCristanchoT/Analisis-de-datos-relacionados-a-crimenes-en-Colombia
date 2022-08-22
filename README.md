# Gestión  de datos
# Taller 1 

### Presentado por:
- Nikolas Rodriguez
- Angie Zapata
- Cristian Cristancho


### 1. Seleccione al menos 4 conjuntos de datos y realice un perfilamiento de cada uno. Describa los hallazgos encontrados en cada conjunto de datos. No olvide mencionar su estructura y aspectos relevantes de calidad como campos nulos, departamentos mal escritos, formatos de fechas incorrectos, entre otros. Si no evidencia ningún problema de calidad de datos, también menciónelo.



Los conjuntos de datos seleccionados para la realización de este taller fueron los siguientes:

- Delitos sexuales
- Extorsión
- Homicidios
- Violencia Intrafamiliar

En general los 4 dataset compartían las siguientes columnas:

| Nombre | Tipo | Descripción |
| ------ | ------ | ------ |
| DEPRTAMENTO | object | Muestra el departamento donde ocurrió el evento | 
| MUNICIPIO | object | Dice el municipio donde ocurrió el hecho | 
| FECHA HECHO | object | Dice el momento en que ocurrió, esta fecha esta segmentada a nivel de días | 
| CANTIDAD |  int64 | La cantidad de personas afectadas | 

En el caso de los datos de delitos sexuales los datos cuentan con 260323, además de que las anteriores columnas están complementadas con las siguientes:

| Nombre | Tipo | Descripción |
| ------ | ------ | ------ |
| CODIGO DANE | float64 | Es una nomenclatura estandarizada, diseñada por el DANE para la identificación de Entidades Territoriales | 
| ARMAS MEDIOS | object | Detalle de las armas empleadas en el evento | 
| GENERO | object | Genero de la victima | 
| GRUPO ETARIO | object | Grupo de edad a la que pertenece la victima | 
| delito | object | Descripción del legal del delito |

En el caso de los datos de extorción hay 69137 registros y estos datos estos están complementados con:

| Nombre | Tipo | Descripción |
| ------ | ------ | ------ |
| COD_DEPTO | int64 | Código del departamento | 
| COD_MUNI | int64 | Código del municipio | 

En homicidios los registros encontrados fueron 59810 y las columnas restantes fueron:

| Nombre | Tipo | Descripción |
| ------ | ------ | ------ |
| CODIGO DANE | float64 | Es una nomenclatura estandarizada, diseñada por el DANE para la identificación de Entidades Territoriales | 
| ARMAS MEDIOS | object | Detalle de las armas empleadas en el evento | 
| GENERO | object | Genero de la victima | 
| GRUPO ETARIO | object | Grupo de edad a la que pertenece la victima | 
| DESCRIPCIÓN CONDUCTA | object | Descripción dada por las autoridades del delito |

Y finalmente en violencia intrafamiliar se encontraron 528880 registros en donde las columnas complementarias son:

| Nombre | Tipo | Descripción |
| ------ | ------ | ------ |
| CODIGO DANE | float64 | Es una nomenclatura estandarizada, diseñada por el DANE para la identificación de Entidades Territoriales | 
| ARMAS MEDIOS | object | Detalle de las armas empleadas en el evento | 
| GENERO | object | Genero de la victima | 
| GRUPO ETARIO | object | Grupo de edad a la que pertenece la victima | 
| DESCRIPCIÓN CONDUCTA | object | Descripción dada por las autoridades del delito |

Ya pasando a los temas relacionados con la calidad de los datos se encontró que, en el dataset de delitos sexuales en la columna de MUNICIPIOS, estos presentan una leve diferencia a la nomenclatura manejada en los otros dataset,

| Municipios en el dataset de violencia | Municipios en los otros dataset  |
| ------ | ------ |
| CARTAGENA (CT) | CARTAGENA |
| VILLAVICENCIO (CT) | VILLAVICENCIO |
| CALI (CT) |CALI |
| RIOHACHA (CT) | RIOHACHA|

Apaarte del caso anterior no hubo mas diferencias o discondancias entre los datos presentados en los registros.

En el caso de los datos faltantes o NaN se realizado un análisis a todos los dataset y se encontraron los siguientes resultados:

###### Delitos sexuales:
&NewLine;
 | Columna | Cantidad de registros nulos |
 | ------ | ------ |
| DEPARTAMENTO    |0|
|MUNICIPIO       |0|
|CODIGO DANE     |0|
|ARMAS MEDIOS    |0|
|FECHA HECHO     |0|
|GENERO          |0|
|GRUPO ETARIO    |0|
|CANTIDAD        |0|

###### Extorcion:
&NewLine;

 | Columna | Cantidad de registros nulos |
 | ------ | ------ |
|FECHA HECHO     |0|
|COD_DEPTO       |0|
|DEPARTAMENTO    |0|
|COD_MUNI        |0|
|MUNICIPIO       |0|
|CANTIDAD        |0|

###### Homicidios:
&NewLine;
 | Columna | Cantidad de registros nulos |
 | ------ | ------ |
|DEPARTAMENTO            |0|
|MUNICIPIO               |0|
|CODIGO DANE             |0|
|ARMAS MEDIOS            |0|
|FECHA HECHO             |0|
|GENERO                  |0|
|GRUPO ETARÍO            |0|
|DESCRIPCIÓN CONDUCTA    |0|
|CANTIDAD                |0|

###### Violencia intrafamiliar:
&NewLine;
 | Columna | Cantidad de registros nulos |
 | ------ | ------ |
 |DEPARTAMENTO      |0|
|MUNICIPIO          |0|
|CODIGO DANE        |0|
|ARMAS MEDIOS       |0|
|FECHA HECHO        |0|
|GENERO             |0|
|GRUPO ETARIO    |1611|
|CANTIDAD           |0|

En los datos que presentaban algun tipo de problema se procedio a eliminar esos registros empleando el comando de pandas:

```python 
violencia_intrafamiliar_df = violencia_intrafamiliar_df.dropna()
```
Y finalmente se estandarizaron las fechas de los dataset al formato datetime64 empleando el siguiete codigo en todos los datsets:

```python 
violencia_intrafamiliar_df['FECHA HECHO'] = pd.to_datetime(violencia_intrafamiliar_df['FECHA HECHO'])
```


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

Lo primero que se hizo en este punto para dar solución al punto, fue unir todos los dataframe que habiamos seleccionado anteriormente y estandarizar los nombres de los municipios y departamentos para agruparlos por dichas columnas y sumar la cantidad de delitos por fecha.

Posteriormente, se hizo el tratamiento del dataframe de tendencia poblacional del DANE seleccionando los años del 2018-2022 que eran los años en los que había información en los demás dataframe, aquí se filtraron los municipios con más de un millón de habitantes, obteniendo como resultado, Bogotá, Medellín, Cali, Barranquilla y Cartagena, las capitales de sus respectivos departamentos. 

Luego para los municipios filtrados se hizo un merge con entre el dataset que reúne la información de los delitos y el de la proyección de la población.

El resultado de la cantidad de delitos a través del tiempo sin normalizar se evidencia en la siguiente gráfica. 

  ![Test Image 2](/img/4cant11.png)

Con el dataset resultante se normalizó la cantidad de delitos con base en la población para el año en curso, obteniendo la siguiente gráfica: 

  ![Test Image 2](/img/4cant21.png)

En la gráfica anterior se puede evindenciar que los municipios con mayor cantidad de crimenes en relación con su población son Bogotá y Medellín, seguidos de Cali y Cartagena y de los Municipios evaluados el que tiene menor indice de criminalidad en los escenarios seleccionados (Violencia inrafamiliar, delitos sexuales, extorción y homicidio) es Barranquilla. 

Se ve con claridad que durante la pandemia se vio una disminución significativa en la cantidad de crimenes, posiblemente por la cuarentena y todos los municipios muestran una tendencia similar a lo largo del tiempo, como se puedo observar en los puntos anteriores. 

### 5. Grabe un video de máximo 5 minutos en donde muestre el proceso realizado y los hallazgos más importantes de los diferentes análisis. Suba el video a YouTube. Todos los integrantes del equipo deben participar en el video.

[![IMAGE ALT TEXT](http://img.youtube.com/vi/XA5RsuITTS4/0.jpg)](http://www.youtube.com/watch?v=XA5RsuITTS4 "Video de presentacion")
