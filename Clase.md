
# ¿Qué es AWS?

Amazon web services
proveedor de servicios en la nube:
    - Servicios de almacenamiento
    - computación
    - bases de datos
    - y muchas más

Es el proveedor de cloud computing más utililizado en el mundo

## Cloud computing

computacion en la nube, es la entrega bajo demanda de recursos y servicios por internet, pagando solo por lo que usamos.

bajo demanda significa que solo se paga por lo que usamos.

este tipo de flexibilidad no es posible si eres administrador propio de estos servicios, en cambio, a aws se le puede solicitar recursos ilimitados pagando por el uso de estos.

## Computacion en la nube y los proveedores de estos

Magic Quadrant for cloud infrastructure and plataform services

1. Amazon web Services (AWS)
2. Microsoft (Azure)
3. Google (Google cloud Plataform)
4. Alibaba cloud
5. Oracle

tienen más de 50% de la demanda general.

aws, es el proveedor mpas utilizado en el mundo.

# Recopilacion de datos

- **Tiempo real**
  - Kinesis Data Streams
  - Simple Queue Services(SQS)
  - Internet of Things
- **Tiempo casi real**
  > Pequeña demora, entre que sucede la acción osea que se genera el dato y que este es recopilado
  - Kinesis Data Firehose (KDF)
  - Database Migration Service (DMS)
- **Lote (Historico)**
En lote, es para un analisis historico, analisis de datos masivo
  - Snowball
  - Data Pipeline

## Recopilación en Tiempo real

- **Kinesis Data Streams**
- Simple Queue Services(SQS)
- Internet of Things

# AWS Kinesis

utilizado para la recopilación de datos, importante para el examen

- alternativa manejada a [Apache Kafka](https://www.redhat.com/es/topics/integration/what-is-apache-kafka)
- ideal par aregristro de aplicaciones, mpetricas,IoT, cliclstreams
- Ideal para big data en tiempo real.
- Exelente para los [**streaming frameworks** (Spark, Nifi, etc)](https://www.upsolver.com/blog/popular-stream-processing-frameworks-compared)
- Los datos se replican automaticamente de forma sicronica a 3 AZ.
  > se replican automatica en 3 zonas de disponibilidad

Kinesis esta compuesto de diferentes servicios como:

- **Kinesis Streams:** ingesta de streaminf de baja latencia a escala
- **Kinesis Analytics:** realiza analisis en tiempo real streams mediante sql
- **Kinesis Firehose o Kinesis data firehose:** carga streams en S3, Redshift, ElasticSearch y Splunk.

## Kinesis Data Stream

  > (Streams= Flujo)

- los streams se dividen en fragmentos/particiones

productor -> fragmentos -> consumidor

- la retencion de los datos es de 24 horas por defecto, puede llegar hasta 365 días.
(entre más tiempo más caro es)
- capacidad de repocesar/reproducir.
- Muchas aplicaciones puede utilizar (consumir) el mismo stream.
- Procesamiento en tiempo real a gran escala.
- **Kinesis no es una base de datos** Una vez que los datos se insertan en Kinesis, no se pueden borrarse (inmutabilidad).
  
### Kinesis Streams Fragmentos

- Un stream esta hecho de muchos fragmentos diferentes
- La facturación es por fragmento, puedes tener tantos como quieras.
- llamadas por lotes o por mensajes.
- El número de fragmentos puede cambiar con el tiempo(con operaciones como reshard y/o merge)
- **Los registros se ordenan por fragmento.**

>siempre se tiene un productor, varios fragmentos y finalmente un consumidor.

#### Kinesis Streams Records

Qué producimos para enviar a nuestros fragmentos.
Producimos lo que se llaman Records (Kinesis Streams Records).

Los Record se componen de:

- Data Blob: datos que se envian, serializados como bytes. Hasta 1 MB.
- Record Key:  
  - enviada junto a un registro, ayuda a agrupar registros en fragmentos. Misma clave-mismo fragmento.
  - Utilizar una clave altamente distribuida para enviar el problema de "partición caliente", donde se envian todos los datos a una misma partición.
- Sequence Number: identificador único par acada registro. Añadido por Kinesis automaticamente depupes de la ingesión.

#### Kinesis Data Streams - Límites

> Necesario saber para el examen.

- **Productor:**
  - 1MB/s o 1000 mensajes/s en escritura por fragmento
  - de lo contrario Se genera  un error de "Provisioned Throughput Exception"

>ProvisionedThroughputExceededException. Message (Excepción de rendimiento aprovisionado. Mensaje): excedió el rendimiento aprovisionado máximo permitido para una tabla o para uno o más índices secundarios globales

- **Consumer Classic:**
  - Limite de 2MB/s en lectura por fragmento en todos los consumidores.
  - Limite 5 llamadas a la API por segundo por fragmento en todos los consumidores.
- **Consumidor Enhanced Fan-Out:** Limite nuevo
  - limite de 2MB/s en lectura por fragmento, por enhanced consumer
  - No se necesitan llamadas a la API (modelo push)
- **Retención de datos:**
  - 24 horas de retención de datos por defecto
  - puede ampliarse a 365 días.

### Producers o productores de Kinesis

Producers o productores es decir varias formas de producir datos a Kinesis data stream como:

- Kinesis SDK
  - permite mandar datos por medio de codigo, o por medio de la cli, que es la Comand Line Interface
- Kinesis Producer Library (KPL)
  - Permite mejorar el rendimiento, utilizando diversas librerias.
- Kinesis Agent
  - Programa de linux que permite enviar registros a Kinesis Data Stream
- Librerias de terceros:
  - Spark, Log4j, Appenders, Flume, Kafka Connect, NiFi
  - todas estas librerias tambien nos permiten enviar datos a Kinesis Data Stream.

#### Kinesis SDK - PutRecord(s)

- Las APIs que se utilizan son PutRectod (uno) y Put Records (muchos)
- PutRecords trabaja por lotes y aumenta el rendimiento - menos peticiones HTTP
- Al sobrepasar los limites sadrá el error  ProvisionedThroughputExeeded si sobrepasamos los limites.
- +AWS SDK móvil: Andriod, IOS, etc.
- ¿Cuando deberiamos utilizar este sistema?**Caso de uso** : bajo rendimiento, mayor latencia API simple, AWS Lambda.
- Fuente de AWS manejadas par aKinesis Data Streams.
  - CloudWatch Logs
  - AWS IoT
  - Kinesis Data Analytics.

#### Error ProvisionedThroughputExeeded

- ProvisionedThroughputExeeded
  - Ocurre cuando se envian más datos (exediendo los MB/s o TPS para cualquier fragmento)
  - Asegúrate de que no tienes un hot shard (fragmento caliente)
    - Ej: si estpy dividiendo los datos por dispositivo y el 90% de los dispositivos son IOS entonces ahí tengo un hot shard.
- Solución:
  - Reintentos con backoff ,por segundos cada dos o 4 segundos realizo un backoff.
  - Aumentar los fragmentos (escalado).
  - Asegúrate de que su clave de partición es buena. Que este bien distribuida y que los datos no se concentren en una de ellas.
  
#### Kinesis Producer Library (KPL)

- Library en  C++ / Java fácil de usar y altamente configurable.
- Se utiliza para construir productores de alto rendimiento y larga duración
- *Tiene automaticamente y configurado un* Mecanismos de reintento automatizado y configurable
- **API síncrona o asíncrona** (mejor rendimiento para la asíncriona)

> si vez en el examen que tenemos que enviar mensajes A kinesis de forma asíncrona, seguramente estamos hablando de la Kinesis producer library (KPL)

- Envia métricas a CloudWatch para su monitorización.
- Batching (ambos activados por defecto) aumentan el rendimiento y disminuyen el coste:
  - Recoge registros y escribe en varios fragmentos la misma llamada a la API **PutRecords**
  - **Aggregate** - Aumento de la altencia
    - Capacidad de almacenar múltiples registros en un solo registro (superar el limite de 1000 registros por segundo)
    - Aumentar el tamaño de la carga útil y mejorar el rendimiento (maximizar el limite de 1 MB/s)
- La comprensión debe ser implementada por el usuario. Tú mismo tienes que realizarlo, no biene por defecto
- Los registros KPL deben decodificarse con KCL o una biblioteca de ayuda especial.

#### Kinesis Producer Library (KPL) - Batching

>concepto importante, que podria salir en el examen.

utilizamos agregate, donde se agregan todos estos registros, y 4 se agregar y se convierten en 1 solo. esta iteración se repite nuevamente, entonces se construyen 2 registros con 4 registros cada uno. estos 2 registros se llaman collection-PutRecords.

Utilizan collectios, para realizar una sola llamada API con PutRecords. entonces de 7 registros que le han llegado solo han echo una sola llamada a la api

Cómo sabe kinesis cuanto tiene que esperar, como junta estos registros.  

- podemos influir en la eficiencia del batching introduciendo algunos retrasos con el **Recod Max Buffered Time** (por defecto 100 ms)
