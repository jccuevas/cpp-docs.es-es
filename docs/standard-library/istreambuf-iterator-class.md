---
title: "istreambuf_iterator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "istreambuf_iterator"
  - "std.istreambuf_iterator"
  - "std::istreambuf_iterator"
  - "streambuf/std::istreambuf_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "istreambuf_iterator (clase)"
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# istreambuf_iterator (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla istreambuf\_iterator describe un objeto de iterador de entrada que extrae elementos de carácter de un búfer de flujos de entrada, al que se accede mediante un objeto que almacena, de tipo puntero a `basic_streambuf`\<**CharType**, **Traits**\>.  
  
## Sintaxis  
  
```  
  
      template <   
   class CharType  
   class Traits = char_traits<CharType>  
>  
class istreambuf_iterator  
: public iterator<input_iterator_tag, CharType, typename Traits::off_type, CharType *, CharType&>  
```  
  
#### Parámetros  
 `CharType`  
 Tipo que representa el tipo de caracteres para istreambuf\_iterator.  
  
 `Traits`  
 Tipo que representa el tipo de caracteres para istreambuf\_iterator.  Este argumento es opcional y el valor predeterminado es `char_traits`\<*CharType\>.*  
  
## Comentarios  
 La clase istreambuf\_iterator debe satisfacer los requisitos de un iterador de entrada.  
  
 Después de crear o de incrementar un objeto de clase istreambuf\_iterator con un puntero almacenado no NULL, el objeto intenta extraer y almacenar un objeto de tipo **CharType** del flujo de entrada asociado.  Sin embargo, la extracción se puede retrasar hasta que el objeto se desreferencia o se copia realmente.  Si se produce un error en la extracción, el objeto reemplaza el puntero almacenado con un puntero NULL, creando de esta forma un indicador de fin de secuencia.  
  
### Constructores  
  
|||  
|-|-|  
|[istreambuf\_iterator](../Topic/istreambuf_iterator::istreambuf_iterator.md)|Construye una clase `istreambuf_iterator` que se inicializa para leer caracteres del flujo de entrada.|  
  
### Typedefs  
  
|||  
|-|-|  
|[char\_type](../Topic/istreambuf_iterator::char_type.md)|Tipo que proporciona el tipo de los caracteres de `ostreambuf_iterator`.|  
|[int\_type](../Topic/istreambuf_iterator::int_type.md)|Tipo que proporciona un tipo entero para `istreambuf_iterator`.|  
|[istream\_type](../Topic/istreambuf_iterator::istream_type.md)|Tipo que proporciona el tipo de flujo de `istream_iterator`.|  
|[streambuf\_type](../Topic/istreambuf_iterator::streambuf_type.md)|Tipo que proporciona el tipo de flujo de `istreambuf_iterator`.|  
|[traits\_type](../Topic/istream_iterator::traits_type.md)|Tipo que proporciona el tipo de rasgos de los caracteres de `istream_iterator`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[equal](../Topic/istreambuf_iterator::equal.md)|Comprueba si dos iteradores de búfer del flujo de entrada son iguales.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\*](../Topic/istreambuf_iterator::operator*.md)|El operador de desreferenciación devuelve el siguiente carácter del flujo.|  
|[operator\+\+](../Topic/istreambuf_iterator::operator++.md)|Devuelve el siguiente carácter del flujo de entrada o copia el objeto antes de incrementarlo y devuelve la copia.|  
|[operator\-\>](../Topic/istreambuf_iterator::operator-%3E.md)|Devuelve el valor de un miembro, si existe.|  
  
## Requisitos  
 **Encabezado:** \<iterator\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [iterator \(Struct\)](../standard-library/iterator-struct.md)   
 [\<iterator\>](../standard-library/iterator.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)