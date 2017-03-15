---
title: "Sugerencias para mejorar c&#243;digo en el que la velocidad de ejecuci&#243;n es importante | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_lfind (función)"
  - "_lsearch (función)"
  - "tareas en segundo plano"
  - "procedimientos recomendados, código para el que es importante la velocidad de ejecución"
  - "bsearch (función)"
  - "caché [C++], aciertos y errores"
  - "pérdidas de ciclos de reloj"
  - "código, importancia de la velocidad de ejecución"
  - "ejecución, mejoras en la velocidad"
  - "asignación en el montón, rendimiento del código para el que es importante la velocidad de ejecución"
  - "funcionamiento de la búsqueda lineal"
  - "listas, ordenar"
  - "funcionamiento del montón local"
  - "memoria [C++], supervisar el uso"
  - "MFC [C++], rendimiento"
  - "optimización [C++], código para el que es importante la velocidad de ejecución"
  - "errores de página"
  - "rendimiento [C++], código para el que es importante la velocidad de ejecución"
  - "programas [C++], rendimiento"
  - "qsort (función)"
  - "buscar [C++], mejorar el rendimiento"
  - "rutinas de ordenación"
  - "ordenar datos, mejorar el rendimiento"
  - "rutinas de ordenación estándar"
  - "subprocesamiento [C++], tareas en segundo plano"
  - "subprocesamiento [C++], procedimientos recomendados"
  - "subprocesamiento [C++], rendimiento"
ms.assetid: 3e95a8cc-6239-48d1-9d6d-feb701eccb54
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Sugerencias para mejorar c&#243;digo en el que la velocidad de ejecuci&#243;n es importante
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para escribir código rápidamente, es necesario comprender todos los aspectos de la aplicación y cómo interactúa con el sistema.  En este tema, se sugieren alternativas a algunas de las técnicas de codificación más obvias para que le resulte más fácil asegurarse de que las partes del código críticas en el tiempo se ejecutan correctamente.  
  
 A modo de resumen, para mejorar el código crítico en el tiempo, tiene que:  
  
-   Saber qué partes del programa deben ser rápidas.  
  
-   Conocer el tamaño y la velocidad del código.  
  
-   Conocer el coste de las nuevas características.  
  
-   Saber cuál es el trabajo mínimo necesario para llevar a cabo el trabajo.  
  
 Para recopilar información sobre el rendimiento del código, puede utilizar el monitor de rendimiento \(perfmon.exe\).  
  
## Secciones de este artículo  
  
-   [Errores de caché y errores de página](#_core_cache_hits_and_page_faults)  
  
-   [Ordenación y búsqueda](#_core_sorting_and_searching)  
  
-   [Bibliotecas de clases y MFC](#_core_mfc_and_class_libraries)  
  
-   [Bibliotecas compartidas](#vcovrsharedlibraries)  
  
-   [Montones](#_core_heaps)  
  
-   [Subprocesos](#_core_threads)  
  
-   [Espacio de trabajo pequeño](#_core_small_working_set)  
  
##  <a name="_core_cache_hits_and_page_faults"></a> Errores de caché y errores de página  
 Los errores de aciertos de caché, tanto en la memoria caché interna como en la externa, y los errores de página \(ir al almacenamiento secundario para obtener datos e instrucciones del programa\) ralentizan el rendimiento de los programas.  
  
 Cada acierto de la caché de la CPU puede costarle a su programa entre 10 y 20 ciclos de reloj.  Cada acierto de la caché externa puede costarle entre 20 y 40 ciclos de reloj.  Un solo error de página puede costarle un millón de ciclos de reloj \(suponiendo que el procesador administre 500 millones de instrucciones por segundo y un tiempo de 2 milisegundos por cada error de página\).  Por lo tanto, lo que más beneficiará a la ejecución del programa será escribir código que reduzca el número de errores de aciertos de caché y errores de página.  
  
 Uno de los motivos por los que algunos programas son lentos es que tienen más errores de página o errores de caché de los necesarios.  Para evitar que esto ocurra, es importante usar estructuras de datos con una buena localidad de referencia, es decir, mantener juntos los elementos relacionados.  A veces, las estructuras de datos que parecen buenas resultan ser horribles debido a una mala localidad de referencia. Otras veces sucede lo contrario.  Dos ejemplos:  
  
-   Las listas vinculadas asignadas dinámicamente pueden reducir el rendimiento del programa porque, al buscar un elemento o atravesar una lista hasta el final, cada vínculo omitido podría tener un error de caché o provocar un error de página.  Si la implementación de la lista se basa en matrices simples, puede resultar mucho más rápida, dado que el almacenamiento en caché es mejor y se producen menos errores de página: incluso teniendo en cuenta que sería más difícil expandir la matriz, es posible que sea más rápida.  
  
-   Las tablas hash que utilizan listas vinculadas asignadas dinámicamente pueden reducir el rendimiento.  Por extensión, las tablas hash que usan listas vinculadas asignadas dinámicamente para almacenar su contenido pueden tener un rendimiento considerablemente peor.  De hecho, en el análisis final, una simple búsqueda lineal a través de una matriz podría ser más rápida \(según las circunstancias\).  Las tablas hash basadas en matrices \(o “hash cerrado”\) son una implementación que se suele pasar por alto y que, a menudo, tiene un rendimiento superior.  
  
##  <a name="_core_sorting_and_searching"></a> Ordenación y búsqueda  
 La ordenación, por naturaleza, requiere bastante tiempo si se compara con muchas operaciones típicas.  La mejor forma de evitar ralentizaciones innecesarias es evitar la ordenación en los momentos críticos.  Es posible que pueda:  
  
-   Aplazar la ordenación hasta un momento en el que el rendimiento no sea crítico.  
  
-   Ordenar los datos en un momento anterior en el que el rendimiento no sea crítico.  
  
-   Ordenar solo la parte de los datos que realmente sea necesario ordenar.  
  
 A veces, se puede generar la lista ya ordenada.  Pero cuidado porque, si necesita insertar datos ya ordenados, puede que requiera una estructura de datos más complicada con una localidad de referencia deficiente, y esto provocaría errores de caché y errores de página.  No hay ningún método que funcione en todos los casos.  Pruebe con varios métodos y mida las diferencias.  
  
 Estas son algunas sugerencias generales para la ordenación:  
  
-   Para minimizar los errores, utilice un orden de existencias.  
  
-   Todo el trabajo que pueda realizar de antemano con el fin de reducir la complejidad de la ordenación valdrá la pena.  Si pasar una sola vez por sus datos sirve para simplificar las comparaciones y reducir la ordenación de O\(n log n\) a O\(n\), casi con toda seguridad saldrá beneficiado.  
  
-   Piense en la localidad de referencia del algoritmo de ordenación y en los datos sobre los que espera que se ejecute.  
  
 Para las búsquedas hay menos alternativas que para la ordenación.  Si la búsqueda es crítica en el tiempo, siempre será mejor usar una búsqueda binaria o una búsqueda en una tabla hash. Sin embargo, como con la ordenación, debe tener en cuenta la localidad.  Una búsqueda lineal a través de una matriz pequeña puede resultar más rápida que una búsqueda binaria a través de una estructura de datos con muchos punteros que provoque errores de página o errores de caché.  
  
##  <a name="_core_mfc_and_class_libraries"></a> Bibliotecas de clases y MFC  
 Las Microsoft Foundation Classes \(MFC\) pueden simplificar en gran medida la escritura de código.  Al escribir código crítico en el tiempo, debe tener presente la sobrecarga inherente a algunas de las clases.  Examine el código MFC empleado por el código crítico en el tiempo para ver si ofrece el rendimiento que necesita.  En la siguiente lista, se identifican las funciones y las clases MFC que debe conocer:  
  
-   `CString` MFC llama a la biblioteca en tiempo de ejecución de C para asignar memoria a una [CString](../../atl-mfc-shared/reference/cstringt-class.md) dinámicamente.  En términos generales, `CString` es tan eficiente como cualquier otra cadena asignada dinámicamente.  Como cualquier cadena asignada dinámicamente, tiene la sobrecarga de la asignación y liberación dinámicas.  A menudo, una simple matriz de `char` en la pila puede cumplir el mismo fin más rápidamente.  No use una `CString` para almacenar una cadena de constante.  Utilice `const char *` en su lugar.  Todas las operaciones que realice con objetos `CString` tendrán cierta sobrecarga.  Puede que sea más rápido usar las [funciones de cadena](../../c-runtime-library/string-manipulation-crt.md) de la biblioteca en tiempo de ejecución.  
  
-   `CArray` Las [CArray](../../mfc/reference/carray-class.md) proporcionan una flexibilidad que no ofrecen las matrices normales, pero puede que su programa no necesite eso.  Si conoce los límites específicos de la matriz, puede utilizar en su lugar una matriz fija global.  Si utiliza `CArray`, use `CArray::SetSize` para establecer su tamaño y especificar el número de elementos que aumentará cuando sea necesaria una reasignación.  Si no lo hace, al agregar elementos, es posible que la matriz se reasigne y se copie con frecuencia: esto es ineficiente y puede fragmentar la memoria.  Tenga en cuenta, también, que si inserta un elemento en una matriz, `CArray` moverá los elementos subsiguientes a la memoria y puede que necesite aumentar la matriz.  Estas acciones pueden provocar errores de caché y errores de página.  Si revisa el código utilizado por MFC, tal vez observe que puede escribir algo más específico para su escenario y, así, mejorar el rendimiento.  Dado que `CArray` es una plantilla, podría, por ejemplo, proporcionar especializaciones de `CArray` para determinados tipos.  
  
-   `CList`  [CList](../../mfc/reference/clist-class.md) es una lista de doble vínculo, así que la inserción de elementos se realiza rápidamente en el encabezado, en el final y en una posición conocida \(`POSITION`\) de la lista.  Sin embargo, para buscar elementos por valor o por índice, es necesaria una búsqueda secuencial, que puede resultar lenta si la lista es larga.  Si su código no requiere una lista de doble vínculo, puede replantearse el uso de `CList`.  Si usa una lista de un solo vínculo, ahorrará la sobrecarga que conlleva actualizar un puntero adicional para todas las operaciones, además de la memoria destinada a ese puntero.  No es que se ahorre muchísima memoria, pero supone otra oportunidad de que aparezcan errores de caché o errores de página.  
  
-   `IsKindOf` Esta función puede generar muchas llamadas y acceder a una gran cantidad de memoria en diferentes áreas de datos, lo que conlleva una localidad de referencia deficiente.  Resulta útil para las versiones de depuración \(en una llamada ASSERT, por ejemplo\), pero trate de evitar usarlo en las versiones de lanzamiento.  
  
-   `PreTranslateMessage` Utilice `PreTranslateMessage` cuando un determinado árbol de ventanas necesite aceleradores del teclado distintos o cuando tenga que insertar la administración de mensajes en el suministro de mensajes.  `PreTranslateMessage` modifica los mensajes de distribución de MFC.  Si invalida `PreTranslateMessage`, hágalo en el nivel que sea necesario.  Por ejemplo, no es necesario que invalide `CMainFrame::PreTranslateMessage` si solo está interesado en los mensajes dirigidos a los elementos secundarios de una vista en particular.  En lugar de ello, invalide `PreTranslateMessage` en la clase de vista.  
  
     No sortee la ruta de acceso de distribución normal con `PreTranslateMessage` para administrar cualquier mensaje que se envíe a cualquier ventana.  Para ello, utilice [procedimientos de ventana](../../mfc/registering-window-classes.md) y mapas de mensajes MFC.  
  
-   `OnIdle` Se pueden producir eventos inactivos en momentos en los que no se lo espere. Por ejemplo, entre los eventos `WM_KEYDOWN` y `WM_KEYUP`.  Los temporizadores pueden ser una forma más eficiente de desencadenar el código.  No fuerce la llamada repetida de `OnIdle` generando mensajes falsos o devolviendo siempre `TRUE` en las invalidaciones de `OnIdle`: si lo hace, no dejará que el subproceso entre en suspensión en ningún momento.  También en este caso, es posible que sea más adecuado usar un temporizador o un subproceso independiente.  
  
##  <a name="vcovrsharedlibraries"></a> Bibliotecas compartidas  
 Es recomendable reutilizar código.  Sin embargo, si va a usar el código de otra persona, debe saber exactamente lo que hace en los casos en los que el rendimiento sea crucial para usted.  La mejor forma de entenderlo es revisar paso por paso el código fuente o realizar mediciones con herramientas como PView o el monitor de rendimiento.  
  
##  <a name="_core_heaps"></a> Montones  
 Si usa varios montones, hágalo con moderación.  Los montones adicionales que se crean con `HeapCreate` y `HeapAlloc` le permiten administrar y, luego, desechar un conjunto relacionado de asignaciones.  No asigne demasiada memoria.  Si va a utilizar varios montones, preste especial atención a la cantidad de memoria que se asignó inicialmente.  
  
 En lugar de usar varios montones, puede emplear funciones auxiliares que hagan de interfaz entre el código y el montón predeterminado.  Las funciones auxiliares facilitan estrategias de asignación personalizadas que pueden mejorar el rendimiento de la aplicación.  Por ejemplo, si realiza asignaciones pequeñas a menudo, puede que le convenga localizar las asignaciones en una parte del montón predeterminado.  Puede asignar un gran bloque de memoria y, después, usar una función auxiliar para subasignar memoria de ese bloque.  Si hace esto, no tendrá montones adicionales con memoria sin usar, porque la asignación saldrá del montón predeterminado.  
  
 Sin embargo, en ciertos casos, usar el montón predeterminado puede reducir la localidad de referencia.  Utilice el Visor de procesos, Spy\+\+ o el monitor de rendimiento para medir los efectos del movimiento de objetos de un montón a otro.  
  
 Mida los montones para comprender cada asignación del montón.  Utilice las [rutinas del montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md) en tiempo de ejecución de C para establecer puntos de control en el montón y volcarlo.  Puede leer la salida en un programa de hojas de cálculo como Microsoft Excel y usar tablas dinámicas para ver los resultados.  Observe el número total de asignaciones, su tamaño y su distribución.  Compárelos con el tamaño de los espacios de trabajo.  Mire también la agrupación en clústeres de los objetos de tamaño relacionado.  
  
 Además, puede usar los contadores de rendimiento para supervisar el uso de memoria.  
  
##  <a name="_core_threads"></a> Subprocesos  
 Para las tareas en segundo plano, si los eventos se administran de manera inactiva y eficiente, se puede lograr más rapidez que con subprocesos.  La localidad de referencia es más fácil de entender en los programas con un solo subproceso.  
  
 Por regla general, solo se usa un subproceso si una notificación del sistema operativo sobre la que se bloquea está en la raíz del trabajo en segundo plano.  En ese caso, la mejor solución es usar subprocesos, porque no resulta práctico bloquear un subproceso principal en un evento.  
  
 Los subprocesos también presentan problemas de comunicación.  Debe administrar el vínculo de comunicación existente entre los subprocesos, con una lista de mensajes o asignando y usando memoria compartida.  Para administrar el vínculo de comunicación, suele ser necesaria la sincronización, con el fin de evitar problemas de interbloqueo y condiciones de carrera.  Esta complejidad puede convertirse fácilmente en errores y problemas de rendimiento.  
  
 Para más información, consulte los temas sobre [procesamiento de bucles inactivos](../../mfc/idle-loop-processing.md) y [multithreading](../../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
##  <a name="_core_small_working_set"></a> Espacio de trabajo pequeño  
 Con los espacios de trabajo menores, se obtienen una localidad de referencia mejor, menos errores de página y más aciertos de caché.  El espacio de trabajo del proceso es la métrica más precisa que ofrece directamente el sistema operativo para medir la localidad de referencia.  
  
-   Para establecer los límites superior e inferior del espacio de trabajo, utilice [SetProcessWorkingSetSize](http://msdn.microsoft.com/library/windows/desktop/ms683226.aspx).  
  
-   Para obtener los límites superior e inferior del espacio de trabajo, utilice [GetProcessWorkingSetSize](http://msdn.microsoft.com/library/windows/desktop/ms686234.aspx).  
  
-   Para ver el tamaño del espacio de trabajo, use Spy\+\+.  
  
## Vea también  
 [Optimizar el código](../../build/reference/optimizing-your-code.md)