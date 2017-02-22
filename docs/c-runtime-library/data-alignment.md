---
title: "Alineaci&#243;n de datos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "data.alignment"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "alineación de datos [C++]"
ms.assetid: 35ac3d2d-a4b3-421b-954f-b7372b1f18e1
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Alineaci&#243;n de datos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las siguientes funciones en tiempo de ejecución de C admiten la alineación de los datos.  
  
### Rutinas de la Dato\-alineación  
  
|Rutina|Utilice|Equivalente de .NET Framework|  
|------------|-------------|-----------------------------------|  
|[\_aligned\_free](../c-runtime-library/reference/aligned-free.md)|Libera un bloque de memoria que fue asignado con [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md)o [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md).|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_aligned\_free\_dbg](../c-runtime-library/reference/aligned-free-dbg.md)|Libera un bloque de memoria que fue asignado con [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) o [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) \(depuración solamente\).|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md)|Asigna memoria en un límite de alineación especificado.|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_aligned\_malloc\_dbg](../c-runtime-library/reference/aligned-malloc-dbg.md)|Asigna memoria en un límite de alineación especificado con el espacio adicional para un encabezado de depuración y sobrescribe los búferes \(versión de depuración solo\).|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_aligned\_msize](../c-runtime-library/reference/aligned-msize.md)|Devuelve el tamaño de un bloque de memoria asignado en el montón.|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_aligned\_msize\_dbg](../c-runtime-library/reference/aligned-msize-dbg.md)|Devuelve el tamaño de un bloque de memoria asignado en el montón \(solo versión de depuración\).|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md)|Asigna memoria en un límite de alineación especificado.|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_aligned\_offset\_malloc\_dbg](../c-runtime-library/reference/aligned-offset-malloc-dbg.md)|Asigna memoria en un límite de alineación especificado \(solo versión de depuración\).|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_aligned\_offset\_realloc](../c-runtime-library/reference/aligned-offset-realloc.md)|Cambia el tamaño de un bloque de memoria que fue asignado con [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) o [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md).|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_aligned\_offset\_realloc\_dbg](../c-runtime-library/reference/aligned-offset-realloc-dbg.md)|Cambia el tamaño de un bloque de memoria que fue asignado con [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) o [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) \(versión de depuración solo\).|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_aligned\_offset\_recalloc](../c-runtime-library/reference/aligned-offset-recalloc.md)|Cambia el tamaño de un bloque de memoria que fue asignado con [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) o [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) e inicializa memoria a 0.|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_aligned\_offset\_recalloc\_dbg](../c-runtime-library/reference/aligned-offset-recalloc-dbg.md)|Cambia el tamaño de un bloque de memoria que fue asignado con [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) o [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) e inicializa memoria a 0 \(versión de depuración solo\).|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_aligned\_realloc](../c-runtime-library/reference/aligned-realloc.md)|Cambia el tamaño de un bloque de memoria que fue asignado con [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) o [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md).|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_aligned\_realloc\_dbg](../c-runtime-library/reference/aligned-realloc-dbg.md)|Cambia el tamaño de un bloque de memoria que fue asignado con [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) o [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) \(versión de depuración solo\).|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_aligned\_recalloc](../c-runtime-library/reference/aligned-recalloc.md)|Cambia el tamaño de un bloque de memoria que fue asignado con [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) o [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) e inicializa memoria a 0.|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_aligned\_recalloc\_dbg](../c-runtime-library/reference/aligned-recalloc-dbg.md)|Cambia el tamaño de un bloque de memoria que fue asignado con [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) o [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) e inicializa memoria a 0 \(versión de depuración solo\).|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)