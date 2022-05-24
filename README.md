# Bienestar en Bogotá, un análisis exhaustivo de las comodidades de los bogotanos utilizando OSM

## Descripción y motivación

¿Se puede utilizar datos de Open Street Maps para medir el bienestar de una ciudad? Este proyecto buscará presentar un análisis del bienestar al que tienen acceso los ciudadanos de Bogotá, Colombia a partir del estudio de la concentración espacial utilizado información de OSM. Este análisis preliminar utilizará la dimensión de *Comidas* (restaurantes, bares, pubs y entre otros) para cuantificar el acceso a bienes y servicios por parte de los bogotanos, sin embargo, como se presenta en los códigos, el algoritmo construido tiene aplicaciones en políticas públicas mucho más profundas que pueden ayudar a los hacedores de política a tomar decisiones. Se estructuró te tal forma que el usuario pueda hacer un *query* de cualquier estructura/edificación en cualquier parte del mundo. Esto tiene aplicación en diferentes sectores institucionales, como por ejemplo salud y económico.

Este proyecto nace por dos razones:
**1. Experiencia personal:** Salgo a recorrer mi zona y no encuentro variedad de establecimientos (cafés, restaurantes o pubs). Siempre debo ir a las mismas zonas (Chapinero, Usaquén) para encontrar "variedad".  
**2.** Hoy en día hay una **brecha entre la demanda y oferta de servicios institucionales (establecimientos económicos, salud, educativos y entre otros).** La demanda de diversas instalaciones aumenta con el crecimiento de la población y las antiguas instalaciones deben actualizarse con el aumento del nivel de vida y las expectativas del público (Rahaman & Siddique, 2020).

## Métodos utilizados 

**1. API:** Para conectarse con OSM debemos hacer uso de la API Overpass API. Esta API permite consultar los datos de OSM según **criterios personalizados de búsqueda** Para ello, cuenta con dos lenguajes de consulta especialmente diseñados: *Overpass XML y Overpass QL.* Estre proyecto utilizó Overpass QL a través de Pyhton.
**2. Administrar, almacenar y limpiar datos:** Todo este análisis se realizó en python. La información se extrajo a través del Overpass API. El análisis se realizó con la librería pandas. Limpieza mas exhaustiva se desarrollo utilizando expresiones regulares y entre otros para limpiar caracteres irregulares. Este primer ejercicio se puede encontrar en el siguiente ((código))[https://github.com/jdmayorga01/bogowelfare/blob/main/Code/Bienestar%20bog.ipynb]. Como resultado se obtuvo una (base de datos)[https://github.com/jdmayorga01/bogowelfare/blob/main/Bases%20de%20datos/OSM%20maps/Final/food.xlsx]; tenga en cuenta que este ejercicio  también se corrió para otros sectores como el educativo y entretenimiento, pero estas bases de datos no fueron utilizadas para el análisis final.

**3. Análisis de los datos:** La base de datos construida pasó por un análisis individual a través del siguiente ((código))[https://github.com/jdmayorga01/bogowelfare/blob/main/Code/An%C3%A1lisis%20comida.ipynb], donde se construyeron bases agregadas y unidas con indicadores económicos de Bogotá (ingresos, población y pobreza, puede encontrar estas bases en el siguiente ((link))[https://github.com/jdmayorga01/bogowelfare/tree/main/Bases%20de%20datos/Datos%20bogot%C3%A1]. 

## Estructura del repositorio

Este repositorio se divide en los siguinetes grupos: 
**1. Código:** En esta carpeta el usuario podrá encontrar los códigos de descarga, limpieza y análisis de los datos de OSM [(link)](https://github.com/jdmayorga01/bogowelfare/blob/main/Code/Bienestar%20bog.ipynb). Adicionalmente, se agrega un código en donde se deja el algoritmo  final para la descarga de datos en OSM [(link)](https://github.com/jdmayorga01/bogowelfare/blob/main/Algoritmo%20final.ipynb). 
**2. Mapas:** Se cargan los datos del shp file de Bogotá que se utilizaron para modelar los outputs
**3. Bases de datos:** En esta carpeta se subirán las bases de datos finales. Adicionalmente, se presenta la información para otros amenities diferentes a *comidas* para presentar pruebas de la capacidad del programa. 

Las bases de datos se dividen en tres: 
* **Datos Bogotá:** Información que se recolectó directamente de datos abiertos o datos abiertos Bogotá. Estan las fuentes originales y las bases de datos limpias. 
* **OSM mapas:** Información a nivel individual por establecimiento (contiene latitud y longitud). Estas bases fueron las que se utilizaron para el análisis. 
* **OSM totales:** Totales de los establecimientos por localidad

**4. Outputs**: En esta carpeta el usuario podrá encontrar los gráficos y tablas que se derivaron del análisis.
