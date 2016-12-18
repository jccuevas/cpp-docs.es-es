---
title: "basic_stringbuf (Clase) | Microsoft Docs"
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
  - "basic_stringbuf"
  - "sstream/std::basic_stringbuf"
  - "std.basic_stringbuf"
  - "std::basic_stringbuf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_stringbuf (clase)"
ms.assetid: 40c85f9e-42a5-4a65-af5c-23c8e3bf8113
caps.latest.revision: 28
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_stringbuf (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un búfer de secuencia que controla la transmisión bidireccional entre elementos de tipo `Elem` —cuyos rasgos de caracteres están determinados por la clase `Tr`— y una secuencia de elementos almacenados en un objeto Array.  
  
## Sintaxis  
  
```  
template <class Elem, class Tr = char_traits<Elem>,   
   class Alloc = allocator<Elem>   
>  
   class basic_stringbuf : public basic_streambuf<Elem, Tr>  
```  
  
#### Parámetros  
 `Alloc`  
 Clase de asignador.  
  
 `Elem`  
 Tipo de elemento básico de la cadena.  
  
 `Tr`  
 Rasgos de caracteres especializados en el elemento básico de la cadena.  
  
## Comentarios  
 El objeto está asignado, extendido y liberado según sea necesario para dar cabida a los cambios en la secuencia.  
  
 Un objeto de clase basic\_stringbuf\<`Elem`, `Tr`, `Alloc`\> almacena una copia del argumento `ios_base::`[openmode](../Topic/ios_base::openmode.md) de su constructor como su `stringbuf` modo **mode**:  
  
-   Si `mode & ios_base::in` es distinto de cero, el búfer de entrada es accesible. Para obtener más información, consulta [basic\_streambuf \(Clase\)](../standard-library/basic-streambuf-class.md).  
  
-   Si `mode & ios_base::out` es distinto de cero, el búfer de salida es accesible.  
  
### Constructores  
  
|||  
|-|-|  
|[basic\_stringbuf](../Topic/basic_stringbuf::basic_stringbuf.md)|Construye un objeto de tipo `basic_stringbuf`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[allocator\_type](../Topic/basic_stringbuf::allocator_type.md)|El tipo es un sinónimo del parámetro de plantilla `Alloc`.|  
|[char\_type](../Topic/basic_stringbuf::char_type.md)|Asocia un nombre de tipo con el parámetro de plantilla `Elem`.|  
|[int\_type](../Topic/basic_stringbuf::int_type.md)|Hace que este tipo en el ámbito de `basic_filebuf` equivalga al tipo con el mismo nombre del ámbito `Tr`.|  
|[off\_type](../Topic/basic_stringbuf::off_type.md)|Hace que este tipo en el ámbito de `basic_filebuf` equivalga al tipo con el mismo nombre del ámbito `Tr`.|  
|[pos\_type](../Topic/basic_stringbuf::pos_type.md)|Hace que este tipo en el ámbito de `basic_filebuf` equivalga al tipo con el mismo nombre del ámbito `Tr`.|  
|[traits\_type](../Topic/basic_stringbuf::traits_type.md)|Asocia un nombre de tipo con el parámetro de plantilla `Tr`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[desbordamiento](../Topic/basic_stringbuf::overflow.md)|Función virtual protegida a la que se puede llamar cuando se inserta un carácter nuevo en un búfer lleno.|  
|[pbackfail](../Topic/basic_stringbuf::pbackfail.md)|La función miembro virtual protegida trata de colocar un elemento en el búfer de entrada y, después, convertirlo en el elemento actual \(indicado por el siguiente puntero\).|  
|[seekoff](../Topic/basic_stringbuf::seekoff.md)|La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas.|  
|[seekpos](../Topic/basic_stringbuf::seekpos.md)|La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas.|  
|[str](../Topic/basic_stringbuf::str.md)|Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.|  
|swap||  
|[underflow](../Topic/basic_stringbuf::underflow.md)|Función miembro virtual protegida que extrae el elemento actual de la secuencia de entrada.|  
  
## Requisitos  
 **Encabezado:** \<sstream\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)