# Estadisticas Youtube

<a href='https://developers.google.com/youtube/v3'><img align='center' alt="Data api v3" src="https://raw.githubusercontent.com/BonfantiMatias/Youtube_Stats/main/assets/youtube.png" height='100px'/>

<br/>

En resumen, este proyecto automatiza la recolección y análisis de estadísticas de canales de YouTube mediante el uso de la "YouTube Data API v3" de GCP y las herramientas de AWS. Permite generar un archivo CSV diariamente, almacenarlo en S3, analizarlo mediante Athena, programado con event bridge y notificar a los usuarios interesados sobre el estado del proyecto mediante SNS.


## YouTube Data API

La recolección de datos se realiza mediante la API de YouTube en GCP. Esta API proporciona una serie de métodos para recopilar información sobre los canales y los videos. Los datos recolectados incluyen información como las visitas, las reproducciones, los comentarios, las suscripciones, etc. El proyecto también esta diseñado para poder seleccionar cuales canales recolectar mediante una lista previamente definida.
<br/>
<img align='left' alt="Api" src="https://raw.githubusercontent.com/BonfantiMatias/Youtube_Stats/main/assets/Api.png"/>
<br/>



## Lambda AWS

La función Lambda es el corazón del proyecto, ya que se encarga de generar un archivo CSV diariamente con los datos necesarios para el análisis. Esta función se ejecuta diariamente a las 21:35, y utiliza una serie de scripts y librerías para recopilar los datos mediante la "YouTube Data API v3" de GCP y escribirlos en un archivo CSV. 

<br/>
<img align='left' alt="Lambda" src="https://github.com/BonfantiMatias/Youtube_Stats/blob/main/assets/lambda.png?raw=true"/>
<br/>



## S3 AWS

Una vez generado el archivo, la función Lambda lo carga automáticamente en un bucket de S3. Esto permite tener una copia de seguridad de los datos y también facilita el acceso a los mismos para su posterior análisis.

<br/>
<img align='left' alt="s31" src="https://github.com/BonfantiMatias/Youtube_Stats/blob/main/assets/S3-1.png?raw=true"/>
<br/>
<br/>
<img align='left' alt="s32" src="https://github.com/BonfantiMatias/Youtube_Stats/blob/main/assets/S3-2.png?raw=true"/>
<br/>

## Athena AWS

Para el análisis de los datos, se utiliza Athena de AWS. Athena es un servicio de consulta SQL que permite ejecutar consultas en los datos almacenados en S3. El proyecto incluye una serie de consultas predefinidas que se ejecutan automáticamente para generar métricas y análisis importantes para el negocio.

<br/>
<img align='left' alt="Athena1" src="https://github.com/BonfantiMatias/Youtube_Stats/blob/main/assets/Athena-1.png?raw=true"/>
<br/>
<br/>
<img align='left' alt="Athena2" src="https://github.com/BonfantiMatias/Youtube_Stats/blob/main/assets/S3-2.png?raw=true"/>
<br/>




## Event bridge AWS

Ademas, se ha programado la función Lambda con event bridge de AWS para ejecutarse diariamente a las 21:35.

<br/>
<img align='left' alt="Event" src="https://github.com/BonfantiMatias/Youtube_Stats/blob/main/assets/Event.png?raw=true"/>
<br/>


## SNS AWS
Por último, se ha incluido en el proyecto un mecanismo de notificación automática mediante SNS (Simple Notification Service) de AWS para informar de la ejecución de la función Lambda y el nombre del archivo que se ha cargado en S3. Esto permite a los usuarios interesados estar al tanto del estado del proyecto y saber cuándo están disponibles los datos para su análisis.

