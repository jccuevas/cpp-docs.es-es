---
title: "&lt;ostream&gt; | Microsoft Docs"
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
  - "std.<ostream>"
  - "<ostream>"
  - "ostream/std::<ostream>"
  - "std::<ostream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ostream (encabezado)"
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
caps.latest.revision: 20
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;ostream&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define la clase de plantilla [basic\_ostream](../standard-library/basic-ostream-class.md), que remite inserciones para iostreams.  El encabezado define también varios manipuladores relacionados.  \(Este encabezado suele incluirlo automáticamente otro encabezado de iostreams.  Rara vez tendrá que incluirlo directamente\).  
  
## Sintaxis  
  
```  
  
#include <ostream>  
  
```  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[ostream](../Topic/ostream.md)|Crea un tipo de `basic_ostream` que está especializado en `char` y `char_traits` especializado en `char`.|  
|[wostream](../Topic/wostream.md)|Crea un tipo de `basic_ostream` que está especializado en `wchar_t` y `char_traits` especializado en `wchar_t`.|  
  
### Manipuladores  
  
|||  
|-|-|  
|[endl](../Topic/endl.md)|Termina una línea y vacía el búfer.|  
|[extremos](../Topic/ends%20\(Standard%20C++%20Library\).md)|Termina una cadena|  
|[flush](../Topic/flush%20\(Standard%20C++%20Library\).md)|Vacía el búfer.|  
||Intercambia los valores del parámetro de objeto `basic_ostream` de la izquierda con los del parámetro del objeto `basic_ostream` de la derecha.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \<\<](../Topic/operator%3C%3C%20\(%3Costream%3E\).md)|Escribe varios tipos en la secuencia.|  
  
### Clases  
  
|||  
|-|-|  
|[basic\_ostream](../standard-library/basic-ostream-class.md)|La clase de plantilla describe un objeto que controla la inserción de objetos codificados y elementos en un búfer de secuencia.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)