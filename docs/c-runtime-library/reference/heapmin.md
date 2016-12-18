---
title: "_heapmin | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_heapmin"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_heapmin"
  - "heapmin"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_heapmin (función)"
  - "memoria de montón"
  - "heapmin (función)"
  - "montones, liberar memoria no utilizada"
  - "memoria, liberación"
  - "minimizar montones"
ms.assetid: c0bccdf6-2d14-4d7b-a7ff-d6a17bdb410f
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _heapmin
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La memoria no utilizada de la pila de libera al sistema operativo.  
  
## Sintaxis  
  
```  
int _heapmin( void );  
```  
  
## Valor devuelto  
 Si es correcto, `_heapmin` devuelve 0; si no, la función devuelve – 1 y establece `errno` a `ENOSYS`.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [\_doserrno, errno, \_sys\_errlist, y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función de `_heapmin` minimiza la pila liberando memoria no utilizada del montón al sistema operativo.  Si el sistema operativo no admite `_heapmin`\(por ejemplo, Ejecutar\), la función devuelve – 1 y establece `errno` a `ENOSYS`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_heapmin`|\<malloc.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [\_heapadd](../../c-runtime-library/heapadd.md)   
 [\_heapchk](../../c-runtime-library/reference/heapchk.md)   
 [\_heapset](../../c-runtime-library/heapset.md)   
 [\_heapwalk](../../c-runtime-library/reference/heapwalk.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)