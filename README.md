# Bienestar en Bogotá, un análisis exhaustivo de las comodidades de los bogotanos utilizando OSM

## Descripción y motivación

¿Se puede utilizar datos de Open Street Maps para medir el bienestar de una ciudad? Este proyecto buscará presentar un análisis del bienestar al que tienen acceso los ciudadanos de Bogotá, Colombia a partir del estudio de la concentración espacial utilizado información de OSM. Este análisis preliminar utilizará la dimensión de *Comidas* (restaurantes, bares, pubs y entre otros) para cuantificar el acceso a bienes y servicios por parte de los bogotanos, sin embargo, como se presenta en los códigos, el algoritmo construido tiene aplicaciones en políticas públicas mucho más profundas que pueden ayudar a los hacedores de política a tomar decisiones. Se estructuró de tal forma que el usuario pueda hacer un *query* (request) de cualquier estructura/edificación en cualquier parte del mundo. Esto tiene aplicación en diferentes sectores institucionales, como por ejemplo salud y económico.

Este proyecto nace por dos razones:
1. **Experiencia personal:** Salgo a recorrer mi zona y no encuentro variedad de establecimientos (cafés, restaurantes o pubs). Siempre debo ir a las mismas zonas (Chapinero, Usaquén) para encontrar "variedad".  

2. Hoy en día hay una **brecha entre la demanda y oferta de servicios institucionales (establecimientos económicos, salud, educativos y entre otros).** La demanda de diversas instalaciones aumenta con el crecimiento de la población y las antiguas instalaciones deben actualizarse con el aumento del nivel de vida y las expectativas del público (Rahaman & Siddique, 2020).

## Métodos utilizados 

1. **API:** Para conectarse con OSM debemos hacer uso de la API Overpass API. Esta API permite consultar los datos de OSM según **criterios personalizados de búsqueda** Para ello, cuenta con dos lenguajes de consulta especialmente diseñados: *Overpass XML y Overpass QL.* Estre proyecto utilizó Overpass QL a través de Pyhton.
2. **Administrar, almacenar y limpiar datos:** Todo este análisis se realizó en python. La información se extrajo a través del Overpass API. El análisis se realizó con la librería pandas. Limpieza mas exhaustiva se desarrollo utilizando expresiones regulares y entre otros para limpiar caracteres irregulares. Este primer ejercicio se puede encontrar en el siguiente [código](https://github.com/jdmayorga01/bogowelfare/blob/main/Code/Bienestar%20bog.ipynb). Como resultado se obtuvo una [base de datos](https://github.com/jdmayorga01/bogowelfare/blob/main/Bases%20de%20datos/OSM%20maps/Final/food.xlsx) que tiene información de cada local de comida en Bogotá con su respectiva longitud y latitud; tenga en cuenta que este ejercicio también se ejecutó para otros sectores como el *educativo y entretenimiento*, pero estas bases de datos no fueron utilizadas para el análisis final.

3. **Análisis de los datos:** La base de datos construida pasó por un análisis individual a través del siguiente [código](https://github.com/jdmayorga01/bogowelfare/blob/main/Code/An%C3%A1lisis%20comida.ipynb), donde se construyeron bases agregadas y se unieron con indicadores económicos de Bogotá (ingresos, población y pobreza, puede encontrar estas bases en el siguiente [link](https://github.com/jdmayorga01/bogowelfare/tree/main/Bases%20de%20datos/Datos%20bogot%C3%A1). Esta base agregada y con información de datos económicos [(link)](https://github.com/jdmayorga01/bogowelfare/blob/main/Bases%20de%20datos/OSM%20maps/Final/food%20merge.xlsx) se extrajo y se guardo en un formato xlsx para ser utilizada en Tableur.
Adicionalmente, en este punto también se hizo un análisis de correlación simple para establecer relaciones.

5. **Análisis gráfico:** Para este punto se utilizó Tableur para analizar las relaciones entre indicadores económicos y ubicación de los locales relacionados a comida. Se utilizó un shape map de las localidades de Bogotá, puede encontrar estas baseses de datos en el siguiente [link](https://github.com/jdmayorga01/bogowelfare/tree/main/Mapas.) Los mapas finales los puede encontrar en el siguiente [link](https://github.com/jdmayorga01/bogowelfare/tree/main/Outputs).

## Resultados

### Totales
- 11.784 observaciones de establecimientos de comida en Bogotá.
- Chapinero es la localidad con mas espacios (alrededor del 20% de los establecimientos).
- Localidades como Usme y Ciudad Bolívar no llegan ni al 2% de las localidades; Esto se puede deber a problemas en la información de OSM porque es muy extraño que una localidad tenga tan pocos establecimientos.

![Totales por localidad](https://user-images.githubusercontent.com/68482485/170110110-0afc9d85-ac5c-430e-ba73-1181b5b1b51c.png)

- En términos del mapa de calor, se puede apreciar que hay una concentración en las zonas de la Candelaria, Chapinero y Teusaquillo.

![Mapa calor individual](https://user-images.githubusercontent.com/68482485/170111285-a7f4bbed-19a5-4a95-a030-12dfc72d4f8f.png)

### Indicadores económicos
Ahora bien, para poder encontrar factores que puedan llegar a explicar esta concentración en ciertas localidades del país se realizó un análisis cruzado con información de Datos Abiertos Bogotá para encontrar correlaciones con el total de establecimientos. Las dimensiones que se evaluaron fueron **población, desigualdades e ingresos** 

![corr matrix](https://user-images.githubusercontent.com/68482485/170113711-ea806430-04c4-4036-bf8f-4fedf5d08c4f.png)

Esta matriz de correlación muestra que hay una fuerte correlación entre pobreza, ingresos. En el caso de la pobreza esta relación es negativa, indicando que los establecimientos se ubican en zonas con menos pobreza. Caso contrario sucede con los ingresos, que tienen una correlación del 0.83, mostrando que los lugares de comida estan mas presentes en localidades con mayor prosperidad económica. 

#### Población 
Para analizar la población se construyó un indice para medir el número de establecimientos por cada 1.000 personas, como se presenta en la siguiente ecuación:

$$Food Index_{loc} = \frac{T. comida_{loc}}{Pob_{loc}}*1.000.$$

![Población leyenda](https://user-images.githubusercontent.com/68482485/170115703-ede2d179-f055-4ea1-8d4c-8b3375fddcd9.png)

Los resultados muestran que La Candelaria tiene alrededor de 31 establecimientos por cada 1.000 personas mientras que Usme solo 0.07, lo que revela la disparidad en el acceso a estos espacios a lo largo de Bogotá. 

#### Pobreza 
![Pobreza leyenda](https://user-images.githubusercontent.com/68482485/170115609-03f7a477-6a6a-4ba4-a922-f109ab687707.png)
La correlación entre pobreza y el total de lugares de comida es de -0.62, se puede apreciar que los lugares de comida estan mucho mas al norte.

#### Ingresos
![Ingresos leyenda](https://user-images.githubusercontent.com/68482485/170115847-d4a65dca-8eb5-4f5a-88cd-6981eb1a774b.png)
La correlación entre ingresos y establecimiento de comida es de 0.83, lo que puede dar indicios de que los establecimientos se ubican en estas localidades por ser zonas con mayor prosperidad económica.

## Estructura del repositorio

Este repositorio se divide en los siguinetes grupos: 
1. **Código:** En esta carpeta el usuario podrá encontrar los códigos de descarga, limpieza y análisis de los datos de OSM [(link)](https://github.com/jdmayorga01/bogowelfare/blob/main/Code/Bienestar%20bog.ipynb). Por otro lado, también se añade un código con las diferentes alternativas que se consideraron para descargar los datos [(link)](https://github.com/jdmayorga01/bogowelfare/blob/main/Code/C%C3%B3digos%20Alternativos.ipynb). Adicionalmente, se agrega un código en donde se deja el algoritmo  final para la descarga de datos en OSM [(link)](https://github.com/jdmayorga01/bogowelfare/blob/main/Algoritmo%20final.ipynb). 
2. **Mapas:** Se cargan los datos del shp file de Bogotá que se utilizaron para modelar los outputs
3. **Bases de datos:** En esta carpeta se subirán las bases de datos finales. Adicionalmente, se presenta la información para otros amenities diferentes a *comidas* para presentar pruebas de la capacidad del programa. 

Las bases de datos se dividen en tres: 
* **Datos Bogotá:** Información que se recolectó directamente de datos abiertos o datos abiertos Bogotá. Estan las fuentes originales y las bases de datos limpias. 
* **OSM mapas:** Información a nivel individual por establecimiento (contiene latitud y longitud). Estas bases fueron las que se utilizaron para el análisis. 
* **OSM totales:** Totales de los establecimientos por localidad. Podrá encontrár el código alternativo que genera estas bases de datos en el siguiente [link](https://github.com/jdmayorga01/bogowelfare/blob/main/Code/C%C3%B3digos%20Alternativos.ipynb).

4. **Outputs**: En esta carpeta el usuario podrá encontrar los gráficos y tablas que se derivaron del análisis.
