---
title: "&lt; istream &gt; | Microsoft Docs"
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
  - "istream/std::<istream>"
  - "std.<istream>"
  - "<istream>"
  - "std::<istream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "istream (encabezado)"
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
caps.latest.revision: 20
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; istream &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define el basic\_istream de clase de plantilla que remita extracciones para las iostreams, y el basic\_iostream de clase de plantilla que remita las inserciones y extracciones. El encabezado define también un manipulador relacionado. Este archivo de encabezado se suele incluir automáticamente mediante otro encabezado de iostreams; rara vez tendrá que incluirlo directamente.  
  
## Sintaxis  
  
```  
  
#include <istream>  
  
```  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[iostream](../Topic/iostream.md)|Tipo `basic_iostream` especializado en `char`.|  
|[istream](../Topic/istream.md)|Tipo `basic_istream` especializado en `char`.|  
|[wiostream](../Topic/wiostream.md)|Tipo `basic_iostream` especializado en **wchar**.|  
|[wistream](../Topic/wistream.md)|Tipo `basic_istream` especializado en **wchar**.|  
  
### Manipuladores  
  
|||  
|-|-|  
|[ws](../Topic/ws.md)|Omite los espacios en blanco en el flujo.|  
|[swap](../Topic/%3Cistream%3E%20swap.md)|Intercambia dos objetos de flujo.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\>\>](../Topic/operator%3E%3E%20\(%3Cistream%3E\).md)|Extrae caracteres y cadenas del flujo.|  
  
### Clases  
  
|||  
|-|-|  
|[basic\_iostream](../standard-library/basic-iostream-class.md)|Clase de secuencia que puede realizar tanto operaciones de entrada como de salida.|  
|[basic\_istream](../standard-library/basic-istream-class.md)|La clase de plantilla describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de flujo con elementos de tipo **Elem**, también conocido como [char\_type](../Topic/basic_ios::char_type.md), cuyos rasgos de caracteres están determinados por la clase **Tr**, también conocida como [traits\_type](../Topic/basic_ios::traits_type.md).|  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)