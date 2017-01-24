---
title: "basic_streambuf (Clase) | Microsoft Docs"
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
  - "basic_streambuf"
  - "streambuf/std::basic_streambuf"
  - "std.basic_streambuf"
  - "std::basic_streambuf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_streambuf (clase)"
ms.assetid: 136af6c3-13bf-4501-9288-b93da26efac7
caps.latest.revision: 27
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_streambuf (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe una clase base abstracta para derivar un búfer de secuencia, que controla la transmisión de elementos a y desde una representación concreta de una secuencia.  
  
## Sintaxis  
  
```  
template<class Elem, class Tr = char_traits<Elem> >  
   class basic_streambuf;  
```  
  
#### Parámetros  
 `Elem`  
 Un [char\_type](../Topic/basic_streambuf::char_type.md).  
  
 `Tr`  
 El carácter [traits\_type](../Topic/basic_streambuf::traits_type.md).  
  
## Comentarios  
 La clase de plantilla describe una clase base abstracta para derivar un búfer de secuencia, que controla la transmisión de elementos a y desde una representación concreta de una secuencia.  Un objeto de clase `basic_streambuf` ayuda a controlar una secuencia con elementos de tipo `Tr`, también conocidos como [char\_type](../Topic/basic_streambuf::char_type.md), cuyos rasgos de caracteres están determinados por la clase [char\_traits](../standard-library/char-traits-struct.md), también conocida como [traits\_type](../Topic/basic_streambuf::traits_type.md).  
  
 Cada búfer de secuencia controla conceptualmente dos secuencias independientes: una para extracciones \(entrada\) y otra para inserciones \(salida\).  Pero una representación específica podría hacer inaccesible una de estas secuencias o las dos.  Normalmente mantiene cierta relación entre las dos secuencias.  Lo que inserta en el flujo de salida de un objeto [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<`Elem`, `Tr`\>, por ejemplo, es lo que extraerá más adelante de su flujo de entrada.  Cuando coloca una secuencia de un objeto [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<`Elem`, `Tr`\>, coloca la otra secuencia en tándem.  
  
 La interfaz pública a la clase de plantilla `basic_streambuf` proporciona las operaciones comunes a todos los búferes de secuencia, independientemente de lo especializados que sean.  La interfaz protegida proporciona las operaciones necesarias para que una representación específica de una secuencia haga su trabajo.  Las funciones miembro virtuales protegidas le permiten personalizar el comportamiento de un búfer de secuencia derivado para una representación específica de una secuencia.  Cada búfer de secuencia derivado de esta biblioteca describe cómo especializa el comportamiento de sus funciones miembro virtuales protegidas.  El comportamiento predeterminado de la clase base, que a menudo consiste en no hacer nada, se describe en este tema.  
  
 Las restantes funciones miembro protegidas controlan las operaciones de copia a y desde cualquier almacenamiento proporcionado para almacenar en búfer las transmisiones a y desde secuencias.  Por ejemplo, un búfer de entrada se caracteriza por:  
  
-   [eback](../Topic/basic_streambuf::eback.md), un puntero al principio del búfer.  
  
-   [gptr](../Topic/basic_streambuf::gptr.md), un puntero al siguiente elemento que se debe leer.  
  
-   [egptr](../Topic/basic_streambuf::egptr.md), un puntero inmediatamente después del final del búfer.  
  
 De forma similar, un búfer de salida se caracteriza por:  
  
-   [pbase](../Topic/basic_streambuf::pbase.md), un puntero al principio del búfer.  
  
-   [pptr](../Topic/basic_streambuf::pptr.md), un puntero al siguiente elemento que se debe escribir.  
  
-   [epptr](../Topic/basic_streambuf::epptr.md), un puntero inmediatamente después del final del búfer.  
  
 Para cualquier búfer, se usa el siguiente protocolo:  
  
-   Si el siguiente puntero es nulo, no existe ningún búfer.  De lo contrario, los tres punteros apuntan a la misma secuencia.  Se puede comparar su orden de forma segura.  
  
-   En el caso de un búfer de salida, si el siguiente puntero tiene, en comparación, un valor menor que el puntero final, puede almacenar un elemento en la posición de escritura designada por el siguiente puntero.  
  
-   En el caso de un búfer de entrada, si el siguiente puntero tiene, en comparación, un valor menor que el puntero final, puede leer un elemento en la posición de lectura designada por el siguiente puntero.  
  
-   En el caso de un búfer de entrada, si el puntero inicial tiene, en comparación, un valor menor que el siguiente puntero, puede devolver un elemento a la posición de devolución designada por el siguiente puntero reducido.  
  
 Todas las funciones miembro virtuales protegidas que escriba para una clase derivada de `basic_streambuf`\<`Elem`, `Tr`\> deben cooperar en el mantenimiento de este protocolo.  
  
 Un objeto de clase `basic_streambuf`\<`Elem`, `Tr`\> almacena los seis punteros descritos anteriormente.  También almacena un objeto de configuración regional en un objeto de tipo [locale](../standard-library/locale-class.md) para su uso potencial por un búfer de secuencia derivado.  
  
### Constructores  
  
|||  
|-|-|  
|[basic\_streambuf](../Topic/basic_streambuf::basic_streambuf.md)|Construye un objeto de tipo `basic_streambuf`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[char\_type](../Topic/basic_streambuf::char_type.md)|Asocia un nombre de tipo con el parámetro de plantilla `Elem`.|  
|[int\_type](../Topic/basic_streambuf::int_type.md)|Asocia un nombre de tipo dentro del ámbito `basic_streambuf` con el parámetro de plantilla `Elem`.|  
|[off\_type](../Topic/basic_streambuf::off_type.md)|Asocia un nombre de tipo dentro del ámbito `basic_streambuf` con el parámetro de plantilla `Elem`.|  
|[pos\_type](../Topic/basic_streambuf::pos_type.md)|Asocia un nombre de tipo dentro del ámbito `basic_streambuf` con el parámetro de plantilla `Elem`.|  
|[traits\_type](../Topic/basic_streambuf::traits_type.md)|Asocia un nombre de tipo con el parámetro de plantilla `Tr`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[eback](../Topic/basic_streambuf::eback.md)|Función protegida que devuelve un puntero al principio del búfer de entrada.|  
|[egptr](../Topic/basic_streambuf::egptr.md)|Función protegida que devuelve un puntero justo después del final del búfer de entrada.|  
|[epptr](../Topic/basic_streambuf::epptr.md)|Función protegida que devuelve un puntero justo después del final del búfer de salida.|  
|[gbump](../Topic/basic_streambuf::gbump.md)|Función protegida que agrega `_Count` al siguiente puntero del búfer de entrada.|  
|[getloc](../Topic/basic_streambuf::getloc.md)|Obtiene la configuración regional del objeto `basic_streambuf`.|  
|[gptr](../Topic/basic_streambuf::gptr.md)|Función protegida que devuelve un puntero al siguiente elemento del búfer de entrada.|  
|[imbue](../Topic/basic_streambuf::imbue.md)|Función protegida virtual a la que llama [pubimbue](../Topic/basic_streambuf::pubimbue.md).|  
|[in\_avail](../Topic/basic_streambuf::in_avail.md)|Devuelve el número de elementos que están listos para ser leídos desde el búfer.|  
|[desbordamiento](../Topic/basic_streambuf::overflow.md)|Función virtual protegida a la que se puede llamar cuando se inserta un carácter nuevo en un búfer lleno.|  
|[pbackfail](../Topic/basic_streambuf::pbackfail.md)|Función miembro virtual protegida que intenta volver a colocar un elemento en el flujo de entrada y convertirlo después en el elemento actual \(indicado por el puntero siguiente\).|  
|[pbase](../Topic/basic_streambuf::pbase.md)|Función protegida que devuelve un puntero al principio del búfer de salida.|  
|[pbump](../Topic/basic_streambuf::pbump.md)|Función protegida que agrega `count` al siguiente puntero del búfer de salida.|  
|[pptr](../Topic/basic_streambuf::pptr.md)|Función protegida que devuelve un puntero al siguiente elemento del búfer de salida.|  
|[pubimbue](../Topic/basic_streambuf::pubimbue.md)|Establece la configuración regional del objeto `basic_streambuf`.|  
|[pubseekoff](../Topic/basic_streambuf::pubseekoff.md)|Llama a [seekoff](../Topic/basic_streambuf::seekoff.md), una función virtual protegida que se invalida en una clase derivada.|  
|[pubseekpos](../Topic/basic_streambuf::pubseekpos.md)|Llama a [seekpos](../Topic/basic_streambuf::seekpos.md), una función virtual protegida que se invalida en una clase derivada y restablece la posición del puntero actual.|  
|[pubsetbuf](../Topic/basic_streambuf::pubsetbuf.md)|Llama a [setbuf](../Topic/basic_streambuf::setbuf.md), una función virtual protegida que se invalida en una clase derivada.|  
|[pubsync](../Topic/basic_streambuf::pubsync.md)|Llama a [sync](../Topic/basic_streambuf::sync.md), una función virtual protegida que se invalida en una clase derivada y actualiza la secuencia externa asociada a este búfer.|  
|[sbumpc](../Topic/basic_streambuf::sbumpc.md)|Lee y devuelve el elemento actual, moviendo el puntero de la secuencia.|  
|[seekoff](../Topic/basic_streambuf::seekoff.md)|La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas.|  
|[seekpos](../Topic/basic_streambuf::seekpos.md)|La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas.|  
|[setbuf](../Topic/basic_streambuf::setbuf.md)|La función miembro virtual protegida realiza una determinada operación para cada búfer de secuencia derivado.|  
|[setg](../Topic/basic_streambuf::setg.md)|Función protegida que almacena `_Gbeg` en el puntero inicial, `_Gnext` en el siguiente puntero y `_Gend` en el puntero final del búfer de entrada.|  
|[setp](../Topic/basic_streambuf::setp.md)|Función protegida que almacena `_Pbeg` en el puntero inicial y `_Pend` en el puntero final del búfer de salida.|  
|[sgetc](../Topic/basic_streambuf::sgetc.md)|Devuelve el elemento actual sin cambiar la posición en la secuencia.|  
|[sgetn](../Topic/basic_streambuf::sgetn.md)|Devuelve el número de elementos leídos.|  
|[showmanyc](../Topic/basic_streambuf::showmanyc.md)|Función miembro virtual protegida que devuelve el recuento del número de caracteres que se puede extraer del flujo de entrada y se asegura de que el programa no estará sujeto a una espera indefinida.|  
|[snextc](../Topic/basic_streambuf::snextc.md)|Lee el elemento actual y devuelve el siguiente elemento.|  
|[sputbackc](../Topic/basic_streambuf::sputbackc.md)|Coloca un `char_type` en la secuencia.|  
|[sputc](../Topic/basic_streambuf::sputc.md)|Coloca un carácter en la secuencia.|  
|[sputn](../Topic/basic_streambuf::sputn.md)|Coloca una cadena de caracteres en la secuencia.|  
|[stossc](../Topic/basic_streambuf::stossc.md)|Mueve más allá del elemento actual de la secuencia.|  
|[sungetc](../Topic/basic_streambuf::sungetc.md)|Obtiene un carácter de la secuencia.|  
|[swap](../Topic/basic_streambuf::swap.md)|Intercambia los valores de este objeto por los valores en el parámetro del objeto `basic_streambuf` proporcionado.|  
|[sync](../Topic/basic_streambuf::sync.md)|Función virtual protegida que intenta sincronizar las secuencias controladas con cualquier secuencia externa asociada.|  
|[uflow](../Topic/basic_streambuf::uflow.md)|Función virtual protegida que extrae el elemento actual del flujo de entrada.|  
|[underflow](../Topic/basic_streambuf::underflow.md)|Función virtual protegida que extrae el elemento actual del flujo de entrada.|  
|[xsgetn](../Topic/basic_streambuf::xsgetn.md)|Función virtual protegida que extrae elementos del flujo de entrada.|  
|[xsputn](../Topic/basic_streambuf::xsputn.md)|Función virtual protegida que inserta elementos en el flujo de salida.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../Topic/basic_streambuf::operator=.md)|Asigna los valores de este objeto desde otro objeto `basic_streambuf`.|  
  
## Requisitos  
 **Encabezado:** \<streambuf\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)