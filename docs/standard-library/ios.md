---
title: "&lt;ios&gt; | Microsoft Docs"
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
  - "std.<ios>"
  - "std::<ios>"
  - "<ios>"
  - "ios/std::<ios>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ios (encabezado)"
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;ios&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define varios tipos y funciones básicos para el funcionamiento de iostreams.  Este encabezado se suele incluir automáticamente mediante otro encabezado de iostreams; rara vez se incluye directamente.  
  
## Sintaxis  
  
```  
  
#include <ios>  
  
```  
  
## Comentarios  
 Un grupo grande de funciones son los manipuladores.  Un manipulador declarado en \<ios\> modifica los valores almacenados en su objeto de argumento de la clase [ios\_base](../standard-library/ios-base-class.md).  Otros manipuladores realizan acciones en flujos controlados por objetos de un tipo derivado de esta clase, tales como una especialización de una de las clases de plantilla [basic\_istream](../standard-library/basic-istream-class.md) o [basic\_ostream](../standard-library/basic-ostream-class.md).  Por ejemplo, [noskipws](../Topic/noskipws.md)\(**str**\) borra la marca de formato `ios_base::skipws` en el objeto **str**, que puede ser de uno de estos tipos.  
  
 También puede llamar a un manipulador insertándolo en un flujo de salida o extrayéndolo de un flujo de entrada, gracias a las operaciones especiales de inserción y extracción proporcionadas para las clases derivadas de `ios_base`.  Por ejemplo:  
  
```  
istr >> noskipws;  
```  
  
 llama a [noskipws](../Topic/noskipws.md)\(**istr**\).  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[ios](../Topic/ios.md)|Es compatible con la clase ios de la antigua biblioteca iostream.|  
|[streamoff](../Topic/streamoff.md)|Admite operaciones internas.|  
|[streampos](../Topic/streampos.md)|Contiene la posición actual del puntero de búfer o el puntero de archivo.|  
|[streamsize](../Topic/streamsize.md)|Especifica el tamaño del flujo.|  
|[wios](../Topic/wios.md)|Es compatible con la clase wios de la antigua biblioteca iostream.|  
|[wstreampos](../Topic/wstreampos.md)|Contiene la posición actual del puntero de búfer o el puntero de archivo.|  
  
### Manipuladores  
  
|||  
|-|-|  
|[boolalpha](../Topic/boolalpha.md)|Especifica que las variables de tipo [bool](../cpp/bool-cpp.md) aparezcan como **true** o **false** en el flujo.|  
|[dec](../Topic/dec.md)|Especifica que las variables de entero aparezcan en notación de base 10.|  
|[defaultfloat](../Topic/%3Cios%3E%20defaultfloat.md)|Configura los indicadores de un objeto `ios_base` para que utilicen un formato de presentación predeterminado para valores float.|  
|[fijo](../Topic/fixed.md)|Especifica que un número de punto flotante se muestre en notación de decimal fijo.|  
|[hex](../Topic/hex.md)|Especifica que las variables de entero aparezcan en notación de base 16.|  
|[internal](../Topic/internal%20\(Standard%20C++%20Library\).md)|Hace que el signo de un número esté justificado a la izquierda y el número se alinee a la derecha.|  
|[izquierda](../Topic/left.md)|Hace que el texto con un ancho menor que el ancho de salida aparezca en el vaciado de flujo con el margen izquierdo.|  
|[noboolalpha](../Topic/noboolalpha.md)|Especifica que las variables de tipo [bool](../cpp/bool-cpp.md) aparezcan como 1 o 0 en el flujo.|  
|[noshowbase](../Topic/noshowbase.md)|Desactiva la opción que indica la base notacional en que se muestra un número.|  
|[noshowpoint](../Topic/noshowpoint.md)|Muestra solo la parte de número entero en los números de punto flotante cuya parte fraccionaria es cero.|  
|[noshowpos](../Topic/noshowpos.md)|Hace que los números positivos no tengan signo explícito.|  
|[noskipws](../Topic/noskipws.md)|Hace que el flujo de entrada lea los espacios.|  
|[nounitbuf](../Topic/nounitbuf.md)|Hace que la salida se almacene en búfer y se procese cuando el búfer esté lleno.|  
|[nouppercase](../Topic/nouppercase.md)|Especifica que los dígitos hexadecimales y el exponente en notación científica aparezcan en minúscula.|  
|[oct](../Topic/oct%20\(%3Cios%3E\).md)|Especifica que las variables de entero aparezcan en notación de base 8.|  
|[derecha](../Topic/right.md)|Hace que el texto con un ancho menor que el ancho de salida aparezca en el vaciado de flujo con el margen derecho.|  
|[científica](../Topic/scientific.md)|Hace que los números de punto flotante se muestren con notación científica.|  
|[showbase](../Topic/showbase.md)|Indica la base notacional en que se muestra un número.|  
|[showpoint](../Topic/showpoint.md)|Muestra la parte de número entero de un número de punto flotante y los dígitos que hay a la derecha del separador decimal, incluso cuando la parte fraccionaria es cero.|  
|[showpos](../Topic/showpos.md)|Hace que los números positivos tengan signo explícito.|  
|[skipws](../Topic/skipws.md)|Hace que el flujo de entrada no lea los espacios.|  
|[unitbuf](../Topic/unitbuf.md)|Hace que la salida se procese cuando el búfer no está lleno.|  
|[mayúsculas](../Topic/uppercase.md)|Especifica que los dígitos hexadecimales y el exponente en notación científica aparezcan en mayúscula.|  
  
### Clases  
  
|||  
|-|-|  
|[basic\_ios](../standard-library/basic-ios-class.md)|La clase de plantilla describe las funciones de almacenamiento y miembro comunes tanto a los flujos de entrada \(de la clase de plantilla [basic\_istream](../standard-library/basic-istream-class.md)\) como a los de salida \(de la clase de plantilla [basic\_ostream](../standard-library/basic-ostream-class.md)\) que dependen de los parámetros de plantilla.|  
|[fpos](../standard-library/fpos-class.md)|La clase de plantilla describe un objeto que puede almacenar toda la información necesaria para restaurar un indicador de posición de archivo arbitraria en cualquier flujo.|  
|[ios\_base](../standard-library/ios-base-class.md)|La clase describe las funciones de almacenamiento y miembro comunes al flujo de entrada y al de salida que no dependen de los parámetros de plantilla.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)