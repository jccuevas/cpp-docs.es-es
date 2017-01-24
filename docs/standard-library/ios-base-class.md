---
title: "ios_base (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ios_base"
  - "std.ios_base"
  - "std::ios_base"
  - "xiosbase/std::ios_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ios_base (clase)"
ms.assetid: 0f9e0abc-f70f-49bc-aa1f-003859f56cfe
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ios_base (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase describe las funciones de almacenamiento y miembro comunes al flujo de entrada y al de salida que no dependen de los parámetros de plantilla.  \(La clase de plantilla [basic\_ios](../standard-library/basic-ios-class.md) describe lo que es común y depende de los parámetros de plantilla\).  
  
 Un objeto de clase ios\_base almacena la información de formato, que consta de:  
  
-   Marcas de formato en un objeto de tipo [fmtflags](../Topic/ios_base::fmtflags.md).  
  
-   Una máscara de excepción en un objeto de tipo [iostate](../Topic/ios_base::iostate.md).  
  
-   Un ancho de campo en un objeto de tipo`int`*.*  
  
-   Una precisión de visualización en un objeto de tipo `int`.  
  
-   Un objeto de configuración regional en un objeto de tipo **locale**.  
  
-   Dos matrices extensibles, con elementos de tipo **long** y puntero `void`.  
  
 Un objeto de clase ios\_base también almacena información de estado de secuencia en un objeto de tipo [iostate](../Topic/ios_base::iostate.md) y una pila de devolución de llamada.  
  
### Constructores  
  
|||  
|-|-|  
|[ios\_base](../Topic/ios_base::ios_base.md)|Construye objetos `ios_base`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[event\_callback](../Topic/ios_base::event_callback.md)|Describe una función que se pasa a [register\_call](../Topic/ios_base::register_callback.md).|  
|[fmtflags](../Topic/ios_base::fmtflags.md)|Constantes para especificar la apariencia de salida.|  
|[iostate](../Topic/ios_base::iostate.md)|Define constantes que describen el estado de una secuencia.|  
|[openmode](../Topic/ios_base::openmode.md)|Describe cómo interactuar con una secuencia.|  
|[seekdir](../Topic/ios_base::seekdir.md)|Especifica el punto de partida para las operaciones de desplazamiento.|  
  
### Enumeraciones  
  
|||  
|-|-|  
|[evento](../Topic/ios_base::event.md)|Especifica tipos de eventos.|  
  
### Constantes  
  
|||  
|-|-|  
|[adjustfield](../Topic/ios_base::fmtflags.md)|Máscara de bits que se define como `internal` &#124; `left` &#124; `right`.|  
|[app](../Topic/ios_base::openmode.md)|Especifica la búsqueda al final de una secuencia antes de cada inserción.|  
|[ate](../Topic/ios_base::openmode.md)|Especifica la búsqueda al final de una secuencia cuando se crea por primera vez su objeto de control.|  
|[badbit](../Topic/ios_base::iostate.md)|Registra una pérdida de integridad del búfer de secuencia.|  
|[basefield](../Topic/ios_base::fmtflags.md)|Máscara de bits que se define como `dec` &#124; `hex` &#124; `oct`.|  
|[beg](../Topic/ios_base::seekdir.md)|Especifica la búsqueda en relación con el principio de una secuencia.|  
|[binaria](../Topic/ios_base::openmode.md)|Especifica que se debe leer un archivo como una secuencia binaria, en lugar de como una secuencia de texto.|  
|[boolalpha](../Topic/ios_base::fmtflags.md)|Especifica la inserción o extracción de objetos de tipo `bool` como nombres \(como `true` y `false`\), en lugar de como valores numéricos.|  
|[cur](../Topic/ios_base::seekdir.md)|Especifica la búsqueda en relación con la posición actual dentro de una secuencia.|  
|[dec](../Topic/ios_base::fmtflags.md)|Especifica la inserción o extracción de valores enteros en formato decimal.|  
|[end](../Topic/ios_base::seekdir.md)|Especifica la búsqueda en relación con el final de una secuencia.|  
|[eofbit](../Topic/ios_base::iostate.md)|Registra el final de archivo al extraer de una secuencia.|  
|[failbit](../Topic/ios_base::iostate.md)|Registra un error al extraer un campo válido de una secuencia.|  
|[fijo](../Topic/ios_base::fmtflags.md)|Especifica la inserción de valores de punto flotante en formato de punto fijo \(sin campo de exponente\).|  
|[floatfield](../Topic/ios_base::fmtflags.md)|Máscara de bits que se define como `fixed` &#124; `scientific`|  
|[goodbit](../Topic/ios_base::iostate.md)|Se borran todos los bits de estado.|  
|[hex](../Topic/ios_base::fmtflags.md)|Especifica la inserción o extracción de valores enteros en formato hexadecimal.|  
|[in](../Topic/ios_base::openmode.md)|Especifica la extracción de una secuencia.|  
|[internal](../Topic/ios_base::fmtflags.md)|Rellena un ancho de campo insertando caracteres de relleno en un punto interno a un campo numérico generado.|  
|[izquierda](../Topic/ios_base::fmtflags.md)|Especifica la justificación a la izquierda.|  
|[oct](../Topic/ios_base::fmtflags.md)|Especifica la inserción o extracción de valores enteros en formato octal.|  
|[out](../Topic/ios_base::openmode.md)|Especifica la inserción en una secuencia.|  
|[derecha](../Topic/ios_base::fmtflags.md)|Especifica la justificación a la derecha.|  
|[científica](../Topic/ios_base::fmtflags.md)|Especifica la inserción de valores de punto flotante en formato científico \(con un campo de exponente\).|  
|[showbase](../Topic/ios_base::fmtflags.md)|Especifica la inserción de un prefijo que revela la base de un campo entero generado.|  
|[showpoint](../Topic/ios_base::fmtflags.md)|Especifica la inserción incondicional de un separador decimal en un campo de punto flotante generado.|  
|[showpos](../Topic/ios_base::fmtflags.md)|Especifica la inserción de un signo más en un campo numérico generado no negativo.|  
|[skipws](../Topic/ios_base::fmtflags.md)|Especifica la omisión del espacio en blanco inicial antes de ciertas extracciones.|  
|[trunc](../Topic/ios_base::openmode.md)|Especifica la eliminación de contenido de un archivo existente cuando se crea su objeto de control.|  
|[unitbuf](../Topic/ios_base::fmtflags.md)|Hace que la salida se vacíe después de cada inserción.|  
|[mayúsculas](../Topic/ios_base::fmtflags.md)|Especifica la inserción de los equivalentes en mayúsculas de letras en minúsculas en ciertas inserciones.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[error](../Topic/ios_base::failure.md)|Clase miembro que actúa como la clase base para todas las excepciones producidas por la función miembro [clear](../Topic/basic_ios::clear.md) en la clase de plantilla [basic\_ios](../standard-library/basic-ios-class.md).|  
|[marcas](../Topic/ios_base::flags.md)|Establece o devuelve la configuración actual de la marca.|  
|[getloc](../Topic/ios_base::getloc.md)|Devuelve el objeto de configuración regional almacenado.|  
|[imbue](../Topic/ios_base::imbue.md)|Cambia la configuración regional.|  
|[Init](../Topic/ios_base::Init.md)|Crea los objetos iostream estándar durante la construcción.|  
|[iword](../Topic/ios_base::iword.md)|Asigna un valor que se va a almacenar como `iword`.|  
|[precisión](../Topic/ios_base::precision.md)|Especifica el número de dígitos que se debe mostrar en un número de punto flotante.|  
|[pword](../Topic/ios_base::pword.md)|Asigna un valor que se va a almacenar como `pword`.|  
|[register\_callback](../Topic/ios_base::register_callback.md)|Especifica una función de devolución de llamada.|  
|[setf](../Topic/ios_base::setf.md)|Establece las marcas especificadas.|  
|[sync\_with\_stdio](../Topic/ios_base::sync_with_stdio.md)|Se asegura de que las operaciones de la biblioteca en tiempo de ejecución de C e iostream se produzcan en el orden en que aparecen en el código fuente.|  
|[unsetf](../Topic/ios_base::unsetf.md)|Hace que las marcas especificadas se desactiven.|  
|[ancho](../Topic/ios_base::width.md)|Establece la longitud del flujo de salida.|  
|[xalloc](../Topic/ios_base::xalloc.md)|Especifica que una variable formará parte de la secuencia.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../Topic/ios_base::operator=.md)|Operador de asignación de objetos `ios_base`.|  
  
## Requisitos  
 **Encabezado:** \<ios\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)