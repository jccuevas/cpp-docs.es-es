---
title: "basic_istringstream (Clase) | Microsoft Docs"
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
  - "std::basic_istringstream"
  - "sstream/std::basic_istringstream"
  - "basic_istringstream"
  - "std.basic_istringstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_istringstream (clase)"
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
caps.latest.revision: 19
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_istringstream (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de secuencia de clase [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\>.  
  
## Sintaxis  
  
```  
  
        template <  
   class Elem,   
   class Tr = char_traits<Elem>,   
   class Alloc = allocator<Elem>   
>  
   class basic_istringstream : public basic_istream<Elem, Tr>  
```  
  
#### Parámetros  
 `Alloc`  
 Clase de asignador.  
  
 `Elem`  
 Tipo de elemento básico de la cadena.  
  
 *Tr*  
 Rasgos de caracteres especializados en el elemento básico de la cadena.  
  
## Comentarios  
 La clase de plantilla describe un objeto que controla la extracción de elementos y objetos codificados desde un búfer de secuencia de clase [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\>, con elementos de tipo **Elem**, cuyos rasgos de caracteres están determinados por la clase **Tr** y cuyos elementos están asignados mediante un asignador de clase `Alloc`.  El objeto almacena un objeto de clase basic\_stringbuf\<**Elem**, **Tr**, `Alloc`\>.  
  
### Constructores  
  
|||  
|-|-|  
|[basic\_istringstream](../Topic/basic_istringstream::basic_istringstream.md)|Construye un objeto de tipo `basic_istringstream`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[allocator\_type](../Topic/basic_istringstream::allocator_type.md)|El tipo es un sinónimo del parámetro de plantilla `Alloc`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[rdbuf](../Topic/basic_istringstream::rdbuf.md)|Devuelve la dirección del búfer de secuencia almacenado de tipo `pointer` a [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<`Elem`, `Tr`, `Alloc`\>.|  
|[str](../Topic/basic_istringstream::str.md)|Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.|  
|[swap](../Topic/basic_istringstream::swap.md)|Intercambia los valores de este objeto `basic_istringstream` con los del objeto proporcionado.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../Topic/basic_istringstream::operator=.md)|Asigna los valores a este objeto `basic_istringstream` desde el parámetro de objeto.|  
  
## Requisitos  
 **Encabezado:** \<sstream\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)