# Amazon Web Services AWS

inicio de secion, se sale cada cieto tiempo

esta la ETL, en aws que es glue.

es un icono con un embudo

## 3 ccosasa importantes

- AWS glue:
	Es la ETL
- S3
- Athen

### Athena
 >Es el mas faicl, se tienien tablas, se le pueden hacer consultas. querys, este es solo vizualización, nada más, el Data SOucer. Es el Catalog.

__Es un visualizador con interfaz de SQL.__


las data Base son fuentes, Para extraer información 

Cada Database, posee tablas

Datamartcobrazas_db, es el que se esta construyendo.

Se puede hacer un 

_Select * from "lo primero entre ""  es la base de datos"."La tabla"
Todos los registros de la tabla "la tabla"_

puede hacer un preview, haciendo clic en la tabla en la región de editor.


### S3:
Donde se esta almacenando los datos, es como la carpetas con los archivos.
Son Folders

Se esta creando el datamar de cobranza: es trabaja con dm

S3 Uri, es la dirección de la carpeta
Analitycs-> Cobranzas ->

Se tienen 3 dimensiones de folders. 
#### Dimensiones
> Registros estacionales como 
> >Cliente, con rut nombre apellido. en el tiempo puede ir creciendo pero tienen dimensiones fijas

#### Tablas de Echo Tablas transacionales:
> Tablas transacionales, facturas

#### Tablas Relacionales:
Realacionan distintas cosas, homologación.

hace el nexo,para que se relacione, valpo y Valparaiso, esos tienene una ID en comun.
La que mantiene la integridad del modelo.


__S3 es lo fisico__
Solo amacena la información en fisico

## Glue:
tiele la estructura logica.
Data bases, cobranza, todas las tablas de dtm de cobranza

Sale la ifnormación logica, es decir qué representa cada columna, como DataType


Ejemplo
  dT DIMENTION TABLE
  tabla FT, FACT TABLE, ESTA RELACIONADA A LAS TABLAS DIMENSIONALES.
co

	id_Transacción, Venta, mes, Fecha
	$2000, 1 ,1/1/2022
	$2500, 1 ,1/1/2022
	$2600, 1 ,1/1/2022
	$4000, 1 ,1/1/2022
	$4000, 1 ,1/1/2022

Query a la base de datos

->TAbla supongamos que la particion por mes y por fecha de venta.

La particion, que aparece en el Glue y en S3
en el GLue aparece como columna. 

La __particion__ siempre esta 100% relacionada a la S3.

path S3 URI, esto me lleva  alas particiones de Folders

El nombre de la particion,se hace por donde estoy mirando los datos.


### la otra parte del glue, son los JOBS

a legacy page:
paginas de legado, 
dentro d elos legacy page, de los jobs, tienes los codigos, que creaaste.


dentro de los pyshart

tienes los cuenta pago. dentro del jobs, tengo información del job, como ver el scrip. 

se puede ejecutar, dentro el mismo Glue de AWS.

se puede ver como se caem los errores.

# tareas.

FTA CUENTA ASOCION CANAL, VOY A VER HARTA IFNROAMCIÓN, REegals de negocio, la tabla,

 Información, de donde bieien


# introducción de Reunion

Enzo los conceptos principales, 

conceptos y tablas principales, de la data

instalar el Py chart y otros programas, que diga cristian.

Como se usa AWS, no esta ligado a vpn.

Enzo muestra los conceptos.

La cobranza explicación, depues se explica el word.

Curso cloud arquitect. No es necesario, se obvia con lo que aprenda.

# Cristian

## Contexo:

2019-2020
Enrique, hizo un datamar, de cobraza, con concpetos, procesos.

despues, en mayo 2022.
Retomar el proceso, dle proyecto,anterior y moverlo a amazon. 
Mayo y junio, rediscovery para modelar correctamente el dat mar.


6 de junio a programar en SQL, python AWS, para construir el datamar.

En la construcción del datamar.

### Que es un datamar

conjunto de datos, que se extraen del datalake.

producto clientes sucursales, siste extr

conjunto de información que se estrae de un datalake, para darle sentido a la iformación.

## DM cñobranzas

- Asignaciones
- Gestiones, de cobranza
.
.
.

se cargan mensualmentre y diario.

Estos 5 ejes se alinean para generar los reportes.

### Cómo conversan.

el mundo de ripley se implemento en amazon.

que cosas de amazon usan

#### Serveless Data lake rfamework Worshop.

usan el SLDF es el framework de amazon que están usando.

es una arquitectura que plantea amazon para generar un datamar, con ciertas caraacteristicas.

te dan todas las recetas, para generar lo que tu quieras. para construir un datamar de forma sencilla


En el SDLF, uno usa la estructura, para construir.

trata de pasar por capas. 

raw, prest stage, strage

normalize,
aqui esta en el transform, 

Glue ETL JOB en puspart.
se trasforma, la data de ripley para poderla llevar a s3

Glue data catalog, se guarda logicamente las  tablas.

DM/DHW
Amazon s3
(Simple, storage,services)

En este servicio, a travez de buckets que son sistema de archivo.

S3. se guardan los archivos. cada carpeta, las servers releas database framework. la arquitectura

(https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/deploy-and-manage-a-serverless-data-lake-on-the-aws-cloud-by-using-infrastructure-as-code.html)[Arquitecuta, o dudas al respecto]

__.parqeuet__,
> es el formato de como se guardan las tablas, que se estan generando.

Athenas, es el servicio, cuando los usarios tienen mucha información, uno para consultarlos se tiene que descargar esos archivos. Amazon Athenas, actua como un motor de sql. para consultar toda la información que se tiene en S3.

Es muy parecido, a transva sql, que es el que usa microsoft.

es muy similar, a mysql


Aca se pueden hacer queris a las tablas.

cuando trabajas con sparq, se trabaja con bloques, se generan los dll. se necesita los interpretes, que lee los archivos.

AWS GLue
es la parte logica.

## qué es un buquet

PPT, de la clase de 
solucion arquitec.

Section introduction
es el lugar, que representa donde permite guardar, archivos("files"), en "Buckets" (Directories)

los objetos (files) tienen una URI o una Key, esta compuesta por un prefix + object name

todos los objetos, tienen una unica key

si se suben mas de 5 gb, se debe usar una erramienta aparte. data mazima es de 5 T.

AWS Glue:
serverless, sofware 

gmail. sofware ass a services, no se preocupa de la mantención. es solo un servicio de uso. 

platform as a services, te dan la plataforma, y tienes ciertas .

lamda es un servicio que puedes geenerar el codigo, y por debajo amaz, te dan las actualizaciones.

Atrick as aservices.(Arquitecture)
S2, se pueden generar maquinas virtuales, ti


Glue, es Sofware as a services.



Glue data catalog, es un catalogo, de datasets.

# buscar jdbc

modo de pysparck


cuando voy a consultar, la información, voy a athena, al catalog, se consulta, la información.
va al amazon s3 y extrae la información.

## CodeCommit en code pipeloine

cuadno se hace un sofware, se debe hacer repositorios, para compartir codigo con tu equipo. para hacer testing.

amazon tiein un micro servicio.

Codecommit, es el repositorio GitHub.

cuando se usa test, o build, se usa
AWS CodeBuild

code pipeloine, el conjunto de todo.

# reomo

RAW datalake

post stage, se saca de aquí la información de ripley.

1° consulto la información de datos en atenas.

me pidieron tal talbla A1. 

voy con atenas, veo que tiene tales consitas.

como recuperare, las cosas de la base de datos, y  genero


el codigo se compone del job y el jabel.

el job es el codio, el jabel es el archivo de configuración que lee el glue, para entender.

el yami, 
yami cual es mi codigo que tengo que ejecutar.

nosotros ejecutamos en el mismo job.

nosotros hacemos el guit up y el guit commit.

abajo, cuando se orquestan las cosas, se empuieza a trabajar el glue jobs.



En el glue, se puede editar y trabajar en los jobs.

deploid SH agarra el codigo py, lo llevahacia el JOB, 

igual hay que actualizar el guit

se envia primero al job, hasta que funciona y cuando funciona se pasa al guit.

# Archivos a instalar 

- [ ] Pycharm Community
- [ ] Anaconda, nuevo ambiente
- [ ] aws CLI
> seria el modo que uno entra a programar en amazon.

Es para interactuar a travez de comandos,

si yo quiero usar por medio de una api, se usa boto3

# Enzo

Recordar el word.

cobranza, esta en clientes, que caen en mora, de 1 dia hasta 180 principalmente, clientes con mala situación financiera.

cosa que el banco le pueda ofrecer más facilidades.

cobranza es tratar de recuperar dinero de los clietnes con una mala situación financiera.

## 

que es busca que el cliente cumpla con sus obligaciones y cancele los montos adeudados.

estrutura
> hay un area encargada de oranizar las cobrantas.
> area encargada de ejecutar la gestion de llamar o mandar mensajes.
> todas estas cñombinacioes, de canales etc. estas se denominan, __estrategias de cobranza__

todos estos medios, de contacto y acercamiento. tambien hay estudios asociados, de cantidad de llamados, leyes que definen la cantidad de contactos que tenemos con el contrario. Estrategias, de calificación de los clientes.
Con 

Etapas de la cobranza

- preventiva
	> tu cuota vence en 5 días más, funciona como recordatorio. para que no quede como moroso. Cuando el cliente 	ueda en mora, hay diferentes etapas
- temprana
  - 1-30 dias de mora
- intermedia/Tardía 
  - 31-90 dias de mora
- Pre-judicial
- Judicial
  - _Castigo_: es cuando la institució asume, que no va a poder recuperar la deuda, esa deuda se califica como incobrarle, se saca del activo y se saca del balace, se asume que no se va a recuperar. cualquier recuperación entra como ingreso directamente. es una figura, que se ve bastante. Hay procesos que son sobre los castigos.
  - entra un tema con abogados, con 


Esto fue a grandes rasgos la cobranza.

>Cada uno delos intentos de contacto, se denomina gestion.

Se pide que guarden cada una de las gestiones, cosa que se puedan registrar cuanto funcioa cada gestión.

Toma un rol importante, para la empresa.

cobranza, lo importante, para definir el ¿como saber si mi proceso de cobranza es eficiente?
para ello se necesitan datos.

tipo de datos:

- caracteristicas dle clietene
- comportamiento crediticio

otros:
-