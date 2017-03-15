---
title: "&lt;strstream&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.<strstream>"
  - "std::<strstream>"
  - "<strstream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strstream (encabezado)"
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;strstream&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define varias clases que admiten operaciones de iostreams en secuencias almacenadas en una matriz asignada de objeto `char`.  Estas secuencias se convierten fácilmente a y desde cadenas de C.  
  
## Sintaxis  
  
```  
  
#include <strstream>  
  
```  
  
## Comentarios  
 Los objetos de tipo `strstream` funcionan con `char` \*, que son cadenas de C.  Utilice [\<sstream\>](../standard-library/sstream.md) para trabajar con objetos de tipo [basic\_string](../standard-library/basic-string-class.md).  
  
> [!NOTE]
>  Las clases de `<strstream>` están en desuso.  Considere el uso de las clases de `<sstream>` en su lugar.  
  
### Clases  
  
|||  
|-|-|  
|[strstreambuf \(Clase\)](../standard-library/strstreambuf-class.md)|La clase describe un búfer de secuencia que controla la transmisión de elementos a y desde una secuencia de elementos almacenados en un objeto de matriz `char`.|  
|[istrstream \(Clase\)](../standard-library/istrstream-class.md)|La clase describe un objeto que controla la extracción de objetos codificados y elementos de un búfer de secuencia de clase [strstreambuf](../standard-library/strstreambuf-class.md).|  
|[ostrstream \(Clase\)](../standard-library/ostrstream-class.md)|La clase describe un objeto que controla la inserción de objetos codificados y elementos en un búfer de secuencia de clase [strstreambuf](../standard-library/strstreambuf-class.md).|  
|[strstream \(Clase\)](../standard-library/strstream-class.md)|La clase describe un objeto que controla la inserción y la extracción de objetos codificados y elementos usando un búfer de secuencia de clase [strstreambuf](../standard-library/strstreambuf-class.md).|  
  
## Vea también  
 [\<strstream\>](../standard-library/strstream.md)   
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)