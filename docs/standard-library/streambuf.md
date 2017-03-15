---
title: "&lt; streambuf &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::<streambuf>"
  - "<streambuf>"
  - "streambuf/std::<streambuf>"
  - "std.<streambuf>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "streambuf (encabezado)"
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# &lt; streambuf &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Incluya el encabezado estándar de iostreams \<streambuf\> para definir la clase de plantilla [basic\_streambuf](../standard-library/basic-streambuf-class.md), que es fundamental para el funcionamiento de las clases iostreams. Este encabezado se suele incluir automáticamente mediante otro de los encabezados de iostreams; rara vez tendrá que incluirlo directamente.  
  
## Sintaxis  
  
```  
  
#include <streambuf>  
  
```  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[streambuf](../Topic/streambuf.md)|Una especialización de `basic_streambuf` que usa `char` como los parámetros de plantilla.|  
|[wstreambuf](../Topic/wstreambuf.md)|Una especialización de `basic_streambuf` que usa `wchar_t` como los parámetros de plantilla.|  
  
### Clases  
  
|||  
|-|-|  
|[basic\_streambuf \(Clase\)](http://msdn.microsoft.com/es-es/d9c706ba-ce01-43e0-b0b2-a558fc53ea8d)|La clase de plantilla describe una clase base abstracta para derivar un búfer de secuencia, que controla la transmisión de elementos a y desde una representación concreta de una secuencia.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)