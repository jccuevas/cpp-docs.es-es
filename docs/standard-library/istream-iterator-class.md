---
title: "istream_iterator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "iterator/std::istream_iterator"
  - "std.istream_iterator"
  - "std::istream_iterator"
  - "istream_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "istream_iterator (clase)"
ms.assetid: fb52a8cd-7f71-48d1-b73e-4b064e2a8d16
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# istream_iterator (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto iterador de entrada.  Extrae objetos de clase `Type` de un flujo de entrada al que tiene acceso a través de un objeto que almacena, de tipo `pointer` en `basic_istream`\<`CharType`, `Traits`\>.  
  
## Sintaxis  
  
```  
template<class Type,  
    class CharType = char,  
    class Traits = char_traits<CharType>,  
    class Distance = ptrdiff_t,  
> class istream_iterator  
 : public iterator<  
        input_iterator_tag,  
        Type,   
        Distance,   
        const Type *,  
        const Type&  
    >;  
```  
  
#### Parámetros  
 `Type`  
 Tipo de objeto que se extraerá del flujo de entrada.  
  
 `CharType`  
 Tipo que representa el tipo de caracteres para `istream_iterator`.  Este argumento es opcional y el valor predeterminado es `char`.  
  
 `Traits`  
 Tipo que representa el tipo de caracteres para `istream_iterator`.  Este argumento es opcional y el valor predeterminado es `char_traits`\<`CharType`\>.  
  
 `Distance`  
 Tipo entero con signo que representa el tipo de diferencia para `istream_iterator`.  Este argumento es opcional y el valor predeterminado es `ptrdiff_t`.  
  
 Después de crear o incrementar un objeto de clase istream\_iterator con un puntero almacenado no null, el objeto intenta extraer y almacenar un objeto de tipo `Type` del flujo de entrada asociado.  Si se produce un error en la extracción, el objeto reemplaza el puntero almacenado con un puntero NULL, creando de esta forma un indicador de fin de secuencia.  
  
### Constructores  
  
|||  
|-|-|  
|[istream\_iterator](../Topic/istream_iterator::istream_iterator.md)|Construye un iterador de fin de secuencia como `istream_iterator` predeterminado, o bien un `istream_iterator` inicializado en el tipo de flujo del iterador del que lee.|  
  
### Typedefs  
  
|||  
|-|-|  
|[char\_type](../Topic/istream_iterator::char_type.md)|Tipo que proporciona el tipo de los caracteres de `istream_iterator`.|  
|[istream\_type](../Topic/istream_iterator::istream_type.md)|Tipo que proporciona el tipo de flujo de `istream_iterator`.|  
|[traits\_type](../Topic/istream_iterator::traits_type.md)|Tipo que proporciona el tipo de rasgos de los caracteres de `istream_iterator`.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\*](../Topic/istream_iterator::operator*.md)|El operador de desreferencia devuelve el objeto almacenado de tipo `Type` señalado por `istream_iterator`.|  
|[operator\-\>](../Topic/istream_iterator::operator-%3E.md)|Devuelve el valor de un miembro, si existe.|  
|[operator\+\+](../Topic/istream_iterator::operator++.md)|Extrae un objeto incrementado del flujo de entrada o copia el objeto antes de aumentarlo y devuelve la copia.|  
  
## Requisitos  
 **Encabezado:** \<iterator\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [input\_iterator\_tag \(Struct\)](../standard-library/input-iterator-tag-struct.md)   
 [iterator \(Struct\)](../standard-library/iterator-struct.md)   
 [\<iterator\>](../standard-library/iterator.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)