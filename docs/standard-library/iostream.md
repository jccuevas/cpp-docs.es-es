---
title: "&lt;iostream&gt; | Microsoft Docs"
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
  - "std.<iostream>"
  - "std::<iostream>"
  - "<iostream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iostream (encabezado)"
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
caps.latest.revision: 23
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;iostream&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Declara los objetos que controlan la lectura y escritura en los flujos estándar.  Suele ser el único encabezado que es necesario incluir para realizar la entrada y salida de un programa de C\+\+.  
  
## Sintaxis  
  
```  
  
#include <iostream>  
  
```  
  
## Comentarios  
 Los objetos se dividen en dos grupos:  
  
-   [cin](../Topic/cin.md), [cout](../Topic/cout.md), [cerr](../Topic/cerr.md) y [clog](../Topic/clog.md) están orientados a bytes y realizan transferencias convencionales byte por byte.  
  
-   [wcin](../Topic/wcin.md), [wcout](../Topic/wcout.md), [wcerr](../Topic/wcerr.md), y [wclog](../Topic/wclog.md) se orientan a caracteres anchos y traducen en ambas direcciones los caracteres anchos que el programa manipula internamente.  
  
 Tras realizar determinadas operaciones en un flujo, como la entrada estándar, no es posible realizar operaciones de orientación en ese mismo flujo.  Por lo tanto, un programa no puede funcionar indistintamente tanto con [cin](../Topic/cin.md) como con [wcin](../Topic/wcin.md), por ejemplo.  
  
 Todos los objetos que se declaran en este encabezado tienen en común una propiedad peculiar: se puede suponer que se construyen antes que cualquier objeto estático que se defina, en una unidad de traducción que incluye \<iostream\>.  De igual forma, se puede suponer que estos objetos no se destruyen antes que los destructores de todos esos objetos estáticos que se definen.  \(Sin embargo, los flujos de salida se vacían durante la finalización del programa\). Por lo tanto, puede leer o escribir sin ningún riesgo en los flujos estándar antes de iniciar el programa y después de la finalización del programa.  
  
 Pero esta garantía no es universal.  Un constructor estático puede llamar a una función en otra unidad de traducción.  La función a la que se llama no puede suponer que se han construido los objetos que se declaran en el encabezado, dada la incertidumbre del orden con el que las unidades de traducción participan en la construcción estática.  Para utilizar esos objetos en este contexto, primero debe construir un objeto de clase [ios\_base::Init](../Topic/ios_base::Init.md).  
  
### Objetos de flujo global  
  
|||  
|-|-|  
|[cerr](../Topic/cerr.md)|Especifica el flujo global `cerr`.|  
|[cin](../Topic/cin.md)|Especifica el flujo global `cin`.|  
|[clog](../Topic/clog.md)|Especifica el flujo global `clog`.|  
|[cout](../Topic/cout.md)|Especifica el flujo global `cout`.|  
|[wcerr](../Topic/wcerr.md)|Especifica el flujo global `wcerr`.|  
|[wcin](../Topic/wcin.md)|Especifica el flujo global `wcin`.|  
|[wclog](../Topic/wclog.md)|Especifica el flujo global `wclog`.|  
|[wcout](../Topic/wcout.md)|Especifica el flujo global `wcout`.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)