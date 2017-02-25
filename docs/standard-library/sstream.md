---
title: "&lt;sstream&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.<sstream>"
  - "std::<sstream>"
  - "<sstream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sstream (encabezado)"
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;sstream&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define varias clases de plantilla que admiten las operaciones con de iostreams en secuencias almacenado en un objeto asignado de la matriz.  Tales secuencias con facilidad se convierten entre objetos de clase de plantilla [basic\_string](../standard-library/basic-string-class.md).  
  
## Sintaxis  
  
```  
namespace std {  
template<class CharType,  
    class Traits = char_traits<CharType>,  
    class Allocator = allocator<CharType> >  
    class basic_stringbuf;  
typedef basic_stringbuf<char> stringbuf;  
typedef basic_stringbuf<wchar_t> wstringbuf;  
  
template<class CharType,  
    class Traits = char_traits<CharType>,  
    class Allocator = allocator<CharType> >  
    class basic_istringstream;  
typedef basic_istringstream<char> istringstream;  
typedef basic_istringstream<wchar_t> wistringstream;  
  
template<class CharType,  
    class Traits = char_traits<CharType>,  
    class Allocator = allocator<CharType> >  
    class basic_ostringstream;  
typedef basic_ostringstream<char> ostringstream;  
typedef basic_ostringstream<wchar_t> wostringstream;  
  
template<class CharType,  
    class Traits = char_traits<CharType>,  
    class Allocator = allocator<CharType> >  
    class basic_stringstream;  
typedef basic_stringstream<char> stringstream;  
typedef basic_stringstream<wchar_t> wstringstream;  
  
        // TEMPLATE FUNCTIONS  
template<class CharType, class Traits, class Allocator>  
    void swap(  
        basic_stringbuf<CharType, Traits, Allocator>& _Left,  
        basic_stringbuf<CharType, Traits, Allocator>& _Right  
    );   
template<class CharType, class Traits, class Allocator>  
    void swap(  
        basic_istringstream<CharType, Traits, Allocator>& _Left,  
        basic_istringstream<CharType, Traits, Allocator>& _Right  
    );  
template<class CharType, class Traits, class Allocator>  
    void swap(  
        basic_ostringstream<CharType, Traits, Allocator>& _Left,  
        basic_ostringstream<CharType, Traits, Allocator>& _Right  
    );  
template<class CharType, class Traits, class Allocator>  
    void swap (  
        basic_stringstream<CharType, Traits, Allocator>& _Left,  
        basic_stringstream<CharType, Traits, Allocator>& _Right  
    );  
}  // namespace std  
  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_Left`|Haga referencia a `sstream` un objeto.|  
|`_Right`|Haga referencia a `sstream` un objeto.|  
  
## Comentarios  
 Los objetos de `char *` tipo pueden usar la funcionalidad de [\<strstream\>](../standard-library/strstream.md) fluir.  Sin embargo, está desusada `<strstream>` y el uso de `<sstream>` se anima.  
  
### Typedefs  
  
|||  
|-|-|  
|[istringstream](../Topic/istringstream.md)|Crea un tipo `basic_istringstream` especializado en un parámetro de plantilla de `char` .|  
|[ostringstream](../Topic/ostringstream.md)|Crea un tipo `basic_ostringstream` especializado en un parámetro de plantilla de `char` .|  
|[stringbuf](../Topic/stringbuf.md)|Crea un tipo `basic_stringbuf` especializado en un parámetro de plantilla de `char` .|  
|[stringstream](../Topic/stringstream.md)|Crea un tipo `basic_stringstream` especializado en un parámetro de plantilla de `char` .|  
|[wistringstream](../Topic/wistringstream.md)|Crea un tipo `basic_istringstream` especializado en un parámetro de plantilla de `wchar_t` .|  
|[wostringstream](../Topic/wostringstream.md)|Crea un tipo `basic_ostringstream` especializado en un parámetro de plantilla de `wchar_t` .|  
|[wstringbuf](../Topic/wstringbuf.md)|Crea un tipo `basic_stringbuf` especializado en un parámetro de plantilla de `wchar_t` .|  
|[wstringstream](../Topic/wstringstream.md)|Crea un tipo `basic_stringstream` especializado en un parámetro de plantilla de `wchar_t` .|  
  
### Manipuladores  
  
|||  
|-|-|  
|[swap](../Topic/%3Csstream%3E%20swap.md)|Cambie los valores entre dos objetos de `sstream` .|  
  
### Clases  
  
|||  
|-|-|  
|[basic\_stringbuf](../standard-library/basic-stringbuf-class.md)|Describe un búfer de la secuencia que controla la transmisión de elementos de **Elem**escrito, cuyos rasgos de carácter se determinan mediante la clase **Tr**, a y desde una secuencia de elementos almacenados en un objeto array.|  
|[basic\_istringstream](../standard-library/basic-istringstream-class.md)|Describe un objeto que controla la recuperación de elementos y objetos codificados de un búfer de la secuencia de la clase [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\>, con los elementos de **Elem**escrito, cuyos rasgos de carácter se determinan mediante la clase **Tr**, y cuyos elementos son asignados por un asignador de la clase `Alloc`.|  
|[basic\_ostringstream](../standard-library/basic-ostringstream-class.md)|Describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de la secuencia de la clase [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\>, con los elementos de **Elem**escrito, cuyos rasgos de carácter se determinan mediante la clase **Tr**, y cuyos elementos son asignados por un asignador de la clase `Alloc`.|  
|[basic\_stringstream](../standard-library/basic-stringstream-class.md)|Describe un objeto que controla la inserción y la recuperación de elementos y objetos codificados mediante un búfer de la secuencia de la clase [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\>, con los elementos de **Elem**escrito, cuyos rasgos de carácter se determinan mediante la clase **Tr**, y cuyos elementos son asignados por un asignador de la clase `Alloc`.|  
  
## Requisitos  
  
-   sstream \<de**Encabezado:** \>  
  
-   **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)