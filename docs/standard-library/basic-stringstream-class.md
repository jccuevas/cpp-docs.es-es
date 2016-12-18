---
title: "basic_stringstream (Clase) | Microsoft Docs"
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
  - "std.basic_stringstream"
  - "basic_stringstream"
  - "std::basic_stringstream"
  - "sstream/std::basic_stringstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_stringstream (clase)"
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
caps.latest.revision: 19
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_stringstream (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que controla la inserción y la extracción de elementos y objetos codificados usando un búfer de secuencia de clase [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\>.  
  
## Sintaxis  
  
```  
  
        template <  
   class Elem,   
   class Tr = char_traits<Elem>,   
   class Alloc = allocator<Elem>   
>  
   class basic_stringstream : public basic_iostream<Elem, Tr>  
```  
  
#### Parámetros  
 `Alloc`  
 Clase de asignador.  
  
 `Elem`  
 Tipo de elemento básico de la cadena.  
  
 *Tr*  
 Rasgos de caracteres especializados en el elemento básico de la cadena.  
  
## Comentarios  
 La clase de plantilla describe un objeto que controla la inserción y extracción de elementos y objetos codificados mediante el uso de un búfer de secuencia de clase [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\>, con elementos de tipo **Elem**, cuyos rasgos de caracteres están determinados por la clase **Tr** y cuyos elementos están asignados mediante un asignador de clase `Alloc`.  El objeto almacena un objeto de clase basic\_stringbuf\<**Elem**, **Tr**, `Alloc`\>.  
  
### Constructores  
  
|||  
|-|-|  
|[basic\_stringstream](../Topic/basic_stringstream::basic_stringstream.md)|Construye un objeto de tipo `basic_stringstream`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[allocator\_type](../Topic/basic_stringstream::allocator_type.md)|El tipo es un sinónimo del parámetro de plantilla `Alloc`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[rdbuf](../Topic/basic_stringstream::rdbuf.md)|Devuelve la dirección del búfer de secuencia almacenado de tipo `pointer` a [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<`Elem`, `Tr`, `Alloc`\>.|  
|[str](../Topic/basic_stringstream::str.md)|Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.|  
  
## Requisitos  
 **Encabezado:** \<sstream\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)