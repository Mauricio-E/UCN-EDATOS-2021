![UCN](images/60x60-ucn-negro.png)


# Informe Técnico 
## Curso: Estructura de datos
### Detección y reidentificación de caras en secuencias de imágenes o video

**Alumnos:**

* Mauricio Espinosa (Lider)


## Resumen 

<Para poder realizar los requerimientos del taller, es preciso antes de comenzar a usar el repositorio Github, comprender detenidamente el funcionamiento general del proyecto, esto incluye un manejo basico de Git (para entender mejor el repositorio GitHub), comprension de aspectos basicos del uso de Visual Studio Code, y manejo del lenguaje C++, esto con el fin de obtener un desarrollo optimo a lo largo de todo el proyecto. El proyecto consta de 11 requerimientos que nos piden medir el trafico de personas que pasan por un lugar, ya sea trafico de entrada, trafico de salida, cantidad de personas por hora (velocidad entrada) que entran, o la cantidad de personas por hora que sale (velocidad de salida), etc., es por ello que el proyecto lo dividiremos en 2 partes, en primer lugar se haran los requerimientos 1-7, y luego para finalizar el proyecto se realizaran los requerimientos 8-11>


## 1. Introducción
Este proyecto se basa en la realizacion de estructuras de datos que nos permite llevar un conteo preciso del ingreso y egreso de personas en un determinado lugar.
-. Se crean diferentes tipos de clases para la ejecucion (Detector.hpp, Detector.cpp, detectedPeople.cpp, Persona.pp, Persona.hpp), todas relacionadas a Clase Persona
-. Estas clases crean objetos que interactuan entre si para poder llevar a cabo el analisis respectivo, en este caso el conteo de ingreso y egresos respectivos.
-. Se utilizan listas enlazadas simples y circulares para almacenar las personas, ya sean que ingresan, egresan, individuales, o cualquier tipo de conteo. Estas listas seran el eje principal de almacenamiento de informacion, ya que al ser secuencial nos permite un optimo almacenamiento, este tipo de estructura de datos es necesaria para la realiazacion de este proyecto.
.- Se utilizan librerias de openCV en todo el proyecto



La primera función de un reporte técnico es plasmar la información necesaria para que otras personas puedan reproducir el sistema propuesto o puedan entender su fucnionamiento . Para cumplir anterior se debe diferenciar claramente entre los artefactos de diseño e implementación. En el caso de un desarrollo tecnológico los algoritmos son importantes como componente de diseño y los programas generalmente son irrelevantes y deben resumidos o agregados en anexos en el documento. Los programas no son importantes en el documento, salvo si se quiere explicar conceptos expecíficos del lenguaje o del algoritmo implementado.

La redacción debe ser formal y de modo impersonal. No se debe utlizar primera persona del singular o plural. Se debe evitar el uso de cualquier calificativo sustituyéndolo siempre utilizando datos concretos y rastreables en documentos o publicaciones a través de referencias bibliográficas. Por ejemplo, no calificar algo como: "muy importante", "sustancial", "muy usadoo" o "mucho mejor".

Las comparaciones deben concretarse con hechos y datos, sin frases ambiguas o términos generales. Por ejemplo, nunca se debe redactar frases como "el método es mejor que el método B". Lo correcto es decir, el error promedio de el método A es de 5 %, correspondiendo a la mitad del error de 10% obtenido utilizando el método B". El tiempo verbal es usualmente presente. No se debe perder de vista que se está explicando ”como hacer algo”, en vez de ”qué se hizo”. Todo aspecto circunstancial es irrelevante para el documento. Por ejemplo, si se ha desarrollado en el laboratorio X, o en el curso Y, con el profesor Z, etc.

### 1.1 Descripción del problema

Dado el laboratorio describir como se entiende el problema bajo sus propias palabras.

### 1.2 Objetivos 

**Construir un sistema que contabilize personas que ingresan y egresan de un determinado lugar a traves de una camara de video**

El fin que se desea llegar. (Comenzar con un verbo: "Construir un sistema...", "Desarrollar un sistema...", etc)

**Objetivos específicos**

1. Instalar efectivamente el compilador, la IDE y el GitHub para el repositorio 
2. El codigo debe cargar y reconocer las imagenes entregadas por el docente
3. Implementar codigo sin errores en la carga de imagenes
4. Contabilizar a traves de estructura de datos las personas que ingresan y egresan a un lugar
5. Manejo de excepcion y discriminacion de informacion de personas en las listas
6. Termino proyecto en tiempo solicitado

Los objetivos específicos son acciones específicas que son desarrolladas para lograr cumplir el objetivo general, por ejemplo:

1. Investigar  el  estado  del  arte  de  visión  por  computador  y  audio  para  resolver  tareas de  clasificación unimodal y multimodal aplicado  al  problema  de  reconocimiento  de emociones.
2.  Seleccionar  uno  o  dos  métodos  estudiados  en  el  estado  del  arte  para  la  estimación  de  laemoción utilizando datos unimodales o multimodales.
3.  Implementar los métodos seleccionados utilizando el lenguaje de programación Python y laslibrerías suministradas por Pytorch.
4.  Validar  los  resultados  por  medio  bases  de  datos  especializadas  para  el  desarrollo  deaplicaciones basadas en la estimación de la emoción y que incluyan varios modos de atributoscomo: imágenes, sonido y/o texto.
5.  Proponer  mejoras  a  los  modelos  implementados  para  mejorar  su  desempeño  en  futurasimplementaciones o proyectos de investigación.
6.  Difundir los resultados en medios científicos nacionales o internacionales.

### 1.3 Solución propuesta

Esbozo de la solución propuesta, se espera que esta vaya evolucionando a medida que se avanza en el proyecto.

## 2. Materiales y métodos

Explicar brevemente como se espera desarrollar el trabajo de implementación.

### 2.1 Instalación

Describir brevemente las librerías utilizadas para la instalación y programas utilizados para la ejecución del código. (Agregar una sección de anexo para describir como fueron instaladas las librerías de OpenCV y la IDE utilzada para el trabajo)

### 2.2 Diseño 

Explicar los componentes (módulos o clases) utilizados para resolver el problema. Indicar arquitectura propuesta, diagrama de clases u otro artefacto que estime conveniente para explicar el diseño de su implimentación.

### 2.3 Implementación

Explicar brevemente algunos aspectos de implementación: Por ejemplo, detector de caras utilizado. Se pueden realizar pequeñas reseñas al código para indicar elementos importantes en el trabajo.

Por ejemplo, 

#### Detector de caras

El detector de caras utilizado fue xxx. Para utilizarlo se debe.... El código para detectar una cara en una imagen se muestra a continuación:

```c++
 1. faceCascadePath = "./haarcascade_frontalface_default.xml";
 2. faceCascade.load( faceCascadePath )
 3. std::vector<Rect> faces;
 4. faceCascade.detectMultiScale(frameGray, faces);

 5. for ( size_t i = 0; i < faces.size(); i++ )
 6. {
 7.  int x1 = faces[i].x;
 8.  int y1 = faces[i].y;
 9.  int x2 = faces[i].x + faces[i].width;
10.  int y2 = faces[i].y + faces[i].height;
11. }
```
La primera linea carga el archivo de entrenamiento... etc

## 3. Resultados obtenidos

## 4. Conclusiones

# Anexos

## Anexo A: Instalación librerías OpenCV

## Anexo B: Instalación de IDE y configuración librerías OpenCV

# Referecia

Indicar los libros, páginas web, documentos, etc. Utilizados en el trabajo. Por ejemplo:

1. MONTERO, J.,Metodos matemáticos aplicados a la ganadería.3aed. Sevilla: Ediciones de la pradera,2007.
2. LVARADO,   J.   P.,¿Qué   debe   contener   un   artículo   científico?.http://www.ie.tec.ac.cr/palvarado/pmwiki/index.php/MSc/Art\%c3\%adculoCient\%c3\%adfico. Fe-cha de acceso:13/Nov/2018


