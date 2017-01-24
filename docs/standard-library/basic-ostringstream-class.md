---
title: "basic_ostringstream (Clase) | Microsoft Docs"
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
  - "basic_ostringstream"
  - "std.basic_ostringstream"
  - "sstream/std::basic_ostringstream"
  - "std::basic_ostringstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_ostringstream (clase)"
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
caps.latest.revision: 19
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_ostringstream (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que controla la inserción de objetos codificados y elementos en un búfer de secuencia de clase [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\>.  
  
## Sintaxis  
  
```  
  
        template <  
   class Elem,   
   class Tr = char_traits<Elem>,   
   class Alloc = allocator<Elem>   
>  
   class basic_ostringstream : public basic_ostream<Elem, Tr>  
```  
  
#### Parámetros  
 `Alloc`  
 Clase de asignador.  
  
 `Elem`  
 Tipo de elemento básico de la cadena.  
  
 *Tr*  
 Rasgos de caracteres especializados en el elemento básico de la cadena.  
  
## Comentarios  
 La clase describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de secuencia, con elementos de tipo **Elem**, cuyos rasgos de caracteres están determinados por la clase **Tr** y cuyos elementos están asignados por un asignador de clase `Alloc`.  El objeto almacena un objeto de clase basic\_stringbuf\<**Elem**, **Tr**, `Alloc`\>.  
  
### Constructores  
  
|||  
|-|-|  
|[basic\_ostringstream](../Topic/basic_ostringstream::basic_ostringstream.md)|Construye un objeto de tipo `basic_ostringstream`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[allocator\_type](../Topic/basic_ostringstream::allocator_type.md)|El tipo es un sinónimo del parámetro de plantilla `Alloc`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[rdbuf](../Topic/basic_ostringstream::rdbuf.md)|Devuelve la dirección del búfer de secuencia almacenado de tipo `pointer` a [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<`Elem`, `Tr`, `Alloc`\>.|  
|[str](../Topic/basic_ostringstream::str.md)|Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.|  
  
## Requisitos  
 **Encabezado:** \<sstream\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)