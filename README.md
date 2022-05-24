# Bienestar en Bogotá, un análisis exhaustivo de las comodidades de los bogotanos utilizando OSM

## Descripción y motivación

¿Se puede utilizar datos de Open Street Maps para medir el bienestar de una ciudad? Este proyecto buscará presentar un análisis del bienestar al que tienen acceso los ciudadanos de Bogotá, Colombia a partir de un análisis de la concentración espacial utilizado información de OSM. Este análisis preliminar utilizará la dimensión de *Comidas* (restaurantes, bares, pubs y entre otros) para cuantificar el acceso a bienes públicos por parte de los bogotanos, sin embargo, como se demuestra con los códigos, el algoritmo construido tiene aplicaciones en políticas públicas mucho más profundas que pueden ayudar a los hacedores de política a tomar decisiones, por ejemplo, para evaluar la concentración espacial de servicios institucionales de salud o económicos.

Este proyecto nace por dos razones:
1. **Experiencia personal:** Salgo a recorrer mi zona y no encuentro variedad de establecimientos (cafés, restaurantes o pubs). Siempre debo ir a las mismas zonas (Chapinero, Usaquén) para encontrar "variedad".  
2. Hoy en día hay una **brecha entre la demanda y oferta de servicios institucionales (establecimientos económicos, salud, educativos y entre otros).** La demanda de diversas instalaciones aumenta con el crecimiento de la población y las antiguas instalaciones deben actualizarse con el aumento del nivel de vida y las expectativas del público (Rahaman & Siddique, 2020).

## Estructura del repositorio

Este repositorio se divide en los siguinetes grupos: 
1. **Código:** En esta carpeta el usuario podrá encontrar los códigos de descarga, limpieza y análisis de los datos de OSM [(link)](https://github.com/jdmayorga01/bogowelfare/blob/main/Code/Bienestar%20bog.ipynb). Adicionalmente, se agrega un código en donde se deja el algoritmo  final para la descarga de datos en OSM [(link)](https://github.com/jdmayorga01/bogowelfare/blob/main/Algoritmo%20final.ipynb). 
2. **Mapas:** Se cargan los datos del shp file de Bogotá que se utilizaron para modelar los outputs
3. **Bases de datos:** En esta carpeta se subirán las bases de datos finales. Adicionalmente, se presenta la información para otros amenities diferentes a *comidas* para presentar pruebas de la capacidad del programa. 

Las bases de datos se dividen en tres: 
* **Datos Bogotá:** Información que se recolectó directamente de datos abiertos o datos abiertos Bogotá. Estan las fuentes originales y las bases de datos limpias. 
* **OSM mapas:** Información a nivel individual por establecimiento (contiene latitud y longitud). Estas bases fueron las que se utilizaron para el análisis. 
* **OSM totales:** Totales de los establecimientos por localidad

4. **Outputs**: En esta carpeta el usuario podrá encontrar los gráficos y tablas que se derivaron del análisis.
