---
title: "&lt;fstream&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::<fstream>"
  - "<fstream>"
  - "std.<fstream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fstream (encabezado)"
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# &lt;fstream&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define varias clases que admiten operaciones de iostreams en secuencias almacenadas en archivos externos.  
  
## Sintaxis  
  
```  
  
#include <fstream>  
  
```  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[filebuf](../Topic/filebuf.md)|Tipo `basic_filebuf` especializado en parámetros de plantilla `char`.|  
|[fstream](../Topic/fstream.md)|Tipo `basic_fstream` especializado en parámetros de plantilla `char`.|  
|[ifstream](../Topic/ifstream.md)|Tipo `basic_ifstream` especializado en parámetros de plantilla `char`.|  
|[ofstream](../Topic/ofstream.md)|Tipo `basic_ofstream` especializado en parámetros de plantilla `char`.|  
|[wfstream](../Topic/wfstream.md)|Tipo `basic_fstream` especializado en parámetros de plantilla `wchar_t`.|  
|[wifstream](../Topic/wifstream.md)|Tipo `basic_ifstream` especializado en parámetros de plantilla `wchar_t`.|  
|[wofstream](../Topic/wofstream.md)|Tipo `basic_ofstream` especializado en parámetros de plantilla `wchar_t`.|  
|[wfilebuf](../Topic/wfilebuf.md)|Tipo `basic_filebuf` especializado en parámetros de plantilla `wchar_t`.|  
  
### Clases  
  
|||  
|-|-|  
|[basic\_filebuf](../standard-library/basic-filebuf-class.md)|La clase de plantilla describe un búfer de secuencia que controla la transmisión de elementos de tipo **Elem**, cuyos rasgos de caracteres están determinados por la clase **Tr**, a y desde una secuencia de elementos almacenados en un archivo externo.|  
|[basic\_fstream](../standard-library/basic-fstream-class.md)|La clase de plantilla describe un objeto que controla la inserción y la extracción de elementos y objetos codificados de un búfer de secuencia de la clase [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**\>, con elementos de tipo **Elem**, cuyos rasgos de caracteres están determinados por la clase **Tr**.|  
|[basic\_ifstream](../standard-library/basic-ifstream-class.md)|La clase de plantilla describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de secuencia de la clase [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**\>, con elementos de tipo **Elem**, cuyos rasgos de caracteres están determinados por la clase **Tr**.|  
|[basic\_ofstream](../standard-library/basic-ofstream-class.md)|La clase de plantilla describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de secuencia de la clase [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**\>, con elementos de tipo **Elem**, cuyos rasgos de caracteres están determinados por la clase **Tr**.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)