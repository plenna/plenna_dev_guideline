# Pautas y estándares para desarrollo en Plenna

Plenna es una Femtech mexicana enfocada en proveer salud integral de la mejor calidad a mujeres. A través de nuestro website, 'Portal Plenna', proveemos información y acceso a salud sexual y los distintos servicios relacionados que proveemos en nuestras clínicas presenciales, las pacientes pueden agendar consultas con nuestras doctoras y tienen acceso al historial médico electrónico de todas las consultas que han tenido con nosotras. Todo esto es posible debido a las plataformas de terceros que integramos a través de sus APIs.

## **Introducción**

Este repositorio contiene las pautas y estándares que utiiza el equipo técnico de Plenna durante el desarrollo de las distintas capas y aplicaciones que conforman el ecosistema digital de Plenna. Sin importar a qué aplicación o componente de la arquitectura se refiera, estos estándares nos ayudan a cumplir los siguientes objetivos:

- Generar código de alta calidad a través de todos nuestros proyectos
- Mantener proyectos donde distintas desarrolladoras pueden trabajar en el mismo código al mismo tiempo
- Generar código con menor probabilidad de bugs y con una documentación que lo hace más fácil de entender
- Reutilizar el código para trabajar más eficientemente, a través de modularización y parametrización
- Mantener un formato y estilo a través de todo el desarrollo, sin importar quién lo desarrolle
- Facilitar el proceso de onboarding de nuevas personas en el equipo

Esta guía es un documento vivo y en constante cambio en el que todas las integrantes del equipo técnico de Plenna pueden colaborar de manera activa.

## **Contenido**

Esta documentación puede dividirse en tres secciones principales:

1. Estándares generales. Aquellos que no son específicos de alguna aplicación o técnología (Front End, Back End, Base de Datos, etc.) sino que deben ser tomados en cuenta para todos los desarrollos y modificaciones a trabajar. Estos pueden encontrarse en este mismo archivo.
2. Estándares de Front End. Pueden encontrarse en la carpeta de 'Front end'.
3. Estándares de Back End. Pueden encontrarse en la carpeta de 'Back end'.

Para los estándares generales:

- [Simplicidad y legibilidad sobre practicidad](#simplicidad-y-legibilidad-sobre-practicidad)
- [Reusabilidad](#reusabilidad)
- [Comentarios](#comentarios)
- [Deuda técnica](#deuda-técnica)

# Pautas y estándares generales

El stack tecnológico de Plenna se basa fuertemente en Javascript al utilizar Express + NodeJS para el back end y React para el front end, por lo que en esta sección se encuentran distintas prácticas relacionadas con este lenguaje y con la manera de trabajar en general.

## **Simplicidad y legibilidad sobre practicidad**

Siempre debe favoreserce la legibilidad del código sobre el performance o la practicidad del mismo. El código difícil de leer, con nombres de variables muy rebuscados o extremadamente cortos que no dan información necesaria, hace que sea más difícil mantenerlo o resolver bugs en él.

Siempre deben utilizarse nombres de variables claros que den información sobre su objetivo y el tipo de información que están almacenando. Aquellas variables temporales, como iteradores o auxiliares, pueden utilizar nombres cortos (`i, j, k, aux`, por ejemplo).

## **Reusabilidad**

Este principio va de la mano del concepto de DRY (Don't repeat yourself). Si identificamos una sección de nuestro código que se repite en distintas partes del proyecto, entonces podemos separarla en un módulo independiente que se reutilice a través del proyecto. Es a través de la modularidad y la parametrización que evitamos repetir las misma líneas de código en el proyecto y que conseguimos componentes reutilizables. Esto nos permite movernos a una mayor velocidad ya que siempre estamso reutilizando las funcionalidades previamente implementadas.

- Modularidad. Desde el diseño de solución, es posible identificar funciones o componentes que son útiles en distintos lugares del proyecto y deben ser módulos independientes. Esto hace el código más fácil de leer y mantener, ya que si se necesita un cambio en esa funcionalidad esta debe realizarse en un sólo lugar.
- Parametrización. Al crear estos componentes reutilizables siempre piensa en todos los posibles escenarios en los que pueden utilizarse, con todos los posibles parámetros o condiciones que pueden recibir y manejando la mayor cantidad posible de errores. De esta manera el componente no dependerá de una situación o variables específicas.

## **Comentarios**

Una de las mejores herramientas de documentación son los comentarios dentro de nuestro código, pero tampoco es buena idea comentar todo nuestro código de manera que se vuelva pesado o complicado de leer. Los comentarios deben utilizarse solamente para enfatizar cosas que no son obvias en el código, enfocándose en el **_por qué_** en vez del **_cómo_**. El **_cómo_** puede llegar a ser obvio por el código mismo, sin embargo, **_por qué_** hicimos las cosas de una manera tiene que ver con nuestra toma de decisiones o las limitaciones que se tenían en un momento específico.

## **Deuda técnica**

En un mundo en el que las tecnologías se mueven tan rápido y cada día tenemos un nuevo framework, una nueva versión de una dependencia o incluso un nuevo requerimiento que nos agrega limitaciones de tiempo, es imposible no tener una dedua técnica eventualmente. La deuda técnica surge de decisiones que tomamos bajo ciertas condiciones para cumplir con deadlines o al descubrir escenarios o problemas que no se tenían contemplados en el diseño de la solución y se traduce en funcionalidades o manejo de errores que queda pendiente de manera temporal para beneficiar la entrega de un feature más grande.

Esta deuda técnica puede llevar a problemas de mantenimiento y nuevos features por lo que es importante tenerlo identificado en todo momento. Agrega comentarios o tags (cuando estemos utilizando paquterías de terceros para documentar) para dejar un mensaje claro de lo que es necesario agregar o arreglar posteriormente, por ejemplo, utilizando comentarios con `//TODO: Tarea por hacer` o `@todo Tarea por hacer` si utilizamos JSDoc.

## **Diseño de solución**

Antes de empezar a desarrollar, es necesario tener una idea clara de a dónde queremos llegar. Es por esto que la primer tarea de un nuevo feature o un proyecto nuevo es el Diseño de solución del mismo, es decir, un plan de cómo alcanzaremos el objetivo planteado.

Este proceso es altamente
