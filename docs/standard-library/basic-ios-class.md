---
title: "basic_ios (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.basic_ios"
  - "ios/std::basic_ios"
  - "basic_ios"
  - "std::basic_ios"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_ios (clase)"
ms.assetid: 4fdcd8e1-62d2-4611-8a70-1e4f58434007
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# basic_ios (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe las funciones de almacenamiento y miembro comunes tanto a los flujos de entrada \(de la clase de plantilla [basic\_istream](../standard-library/basic-istream-class.md)\) como a los de salida \(de la clase de plantilla [basic\_ostream](../standard-library/basic-ostream-class.md)\) que dependen de los parámetros de plantilla.  \(La clase [ios\_base](../standard-library/ios-base-class.md) describe lo que es común y no depende de los parámetros de plantilla\). Un objeto de clase **basic\_ios\<class Elem, class Traits\>** ayuda a controlar una secuencia con elementos de tipo **Elem**, cuyos rasgos de carácter están determinados por la clase **Traits**.  
  
## Sintaxis  
  
```  
  
     template <class   
     Elem  
     , class   
     Traits  
     >  
class basic_ios : public ios_base  
```  
  
#### Parámetros  
 `Elem`  
 Un tipo.  
  
 `Traits`  
 Una variable de tipo `char_traits`.  
  
## Comentarios  
 Un objeto de clase **basic\_ios\<clase Elem, class Traits\>** almacena:  
  
-   Un puntero de empate a un objeto de tipo [basic\_istream](../standard-library/basic-istream-class.md)**\<Elem, Traits\>**.  
  
-   Un puntero de búfer de secuencia a un objeto de tipo [basic\_streambuf](../standard-library/basic-streambuf-class.md)**\<Elem, Traits \>**.  
  
-   [Información de formato](../standard-library/ios-base-class.md).  
  
-   [Información de estado de la secuencia](../standard-library/ios-base-class.md) en un objeto de base de tipo [ios\_base](../standard-library/ios-base-class.md).  
  
-   Un carácter de relleno en un objeto de tipo `char_type`.  
  
### Constructores  
  
|||  
|-|-|  
|[basic\_ios](../Topic/basic_ios::basic_ios.md)|Construye la clase `basic_ios`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[char\_type](../Topic/basic_ios::char_type.md)|Sinónimo del parámetro de plantilla `Elem`.|  
|[int\_type](../Topic/basic_ios::int_type.md)|Sinónimo de `Traits::int_type`.|  
|[off\_type](../Topic/basic_ios::off_type.md)|Sinónimo de `Traits::off_type`.|  
|[pos\_type](../Topic/basic_ios::pos_type.md)|Sinónimo de `Traits::pos_type`.|  
|[traits\_type](../Topic/basic_ios::traits_type.md)|Sinónimo del parámetro de plantilla `Traits`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[bad](../Topic/basic_ios::bad.md)|Indica una pérdida de integridad del búfer de secuencia.|  
|[desactivada](../Topic/basic_ios::clear.md)|Borra todas las marcas de error.|  
|[copyfmt](../Topic/basic_ios::copyfmt.md)|Copia las marcas de una secuencia a otra.|  
|[eof](../Topic/basic_ios::eof.md)|Indica si se ha alcanzado el extremo de una secuencia.|  
|[excepciones](../Topic/basic_ios::exceptions.md)|Indica qué excepciones iniciará la secuencia.|  
|[fail](../Topic/basic_ios::fail.md)|Indica un error al extraer un campo válido de una secuencia.|  
|[fill](../Topic/basic_ios::fill.md)|Especifica o devuelve el carácter que se usará si el texto no tiene el mismo ancho que la secuencia.|  
|[good](../Topic/basic_ios::good.md)|Indica que la secuencia está en buen estado.|  
|[imbue](../Topic/basic_ios::imbue.md)|Cambia la configuración regional.|  
|[init](../Topic/basic_ios::init.md)|Llamada por constructores `basic_ios`.|  
|[move](../Topic/basic_ios::move.md)|Mueve todos los valores, excepto el puntero al búfer de secuencia, desde el parámetro hasta el objeto actual.|  
|[narrow](../Topic/basic_ios::narrow.md)|Busca el carácter equivalente a un determinado `char_type`.|  
|[rdbuf](../Topic/basic_ios::rdbuf.md)|Redirige la secuencia al búfer especificado.|  
|[rdstate](../Topic/basic_ios::rdstate.md)|Lee el estado de bits de las marcas.|  
|[set\_rdbuf](../Topic/basic_ios::set_rdbuf.md)|Asigna un búfer de secuencia para que sea el búfer de lectura de este objeto de secuencia.|  
|[setstate](../Topic/basic_ios::setstate.md)|Establece marcas adicionales.|  
|[swap](../Topic/basic_ios::swap.md)|Cambia los valores de este objeto `basic_ios` por los de otro objeto `basic_ios`.  No se intercambian los punteros a los búferes de secuencia.|  
|[tie](../Topic/basic_ios::tie.md)|Se asegura de que una secuencia se procese antes que otra.|  
|[widen](../Topic/basic_ios::widen.md)|Busca el `char_type` equivalente a un determinado carácter.|  
  
### Operadores  
  
|||  
|-|-|  
|[explicit operator bool](../Topic/basic_ios::operator%20bool.md)|Permite el uso de un objeto `basic_ios` como un `bool`.  La conversión automática de tipo está deshabilitada para evitar efectos secundarios típicos no deseados.|  
|[operator void \*](../Topic/basic_ios::operator%20void%20*.md)|Indica si la secuencia sigue siendo aceptable.|  
|[operador \!](../Topic/basic_ios::operator!.md)|Indica si la secuencia no es inaceptable.|  
  
## Requisitos  
 **Encabezado:** \<ios\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)