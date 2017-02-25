---
title: "_heapadd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_heapadd"
apilocation: 
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr80.dll"
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "heapadd"
  - "_heapadd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_heapadd (función)"
  - "heapadd (función)"
  - "montones, agregar memoria"
  - "memoria, agregar a montones"
ms.assetid: 4d691fe2-2763-49f4-afb1-62738b7cd3ff
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _heapadd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Agrega memoria al montón.  
  
> [!IMPORTANT]
>  Esta función está obsoleta. A partir de Visual Studio 2015, no está disponible en CRT.  
  
## Sintaxis  
  
```  
int _heapadd(   
   void *memblock,  
   size_t size   
);  
```  
  
#### Parámetros  
 `memblock`  
 Puntero a la memoria del montón.  
  
 `size`  
 Tamaño de la memoria que se agregará, en bytes.  
  
## Valor devuelto  
 Si se realiza correctamente, `_heapadd` devuelve 0; en caso contrario, la función devuelve –1 y establece `errno` en `ENOSYS`.  
  
 Para más información sobre este y otros códigos de retorno, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 A partir de la versión 4.0 de Visual C\+\+, la estructura del montón subyacente se movió a las bibliotecas de tiempo en ejecución de C para admitir las nuevas características de depuración. Como resultado, `_heapadd` ya no se admite en ninguna plataforma que se base en la API de Win32.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_heapadd`|\<malloc.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../c-runtime-library/memory-allocation.md)   
 [free](../c-runtime-library/reference/free.md)   
 [\_heapchk](../c-runtime-library/reference/heapchk.md)   
 [\_heapmin](../c-runtime-library/reference/heapmin.md)   
 [\_heapset](../c-runtime-library/heapset.md)   
 [\_heapwalk](../c-runtime-library/reference/heapwalk.md)   
 [malloc](../c-runtime-library/reference/malloc.md)   
 [realloc](../c-runtime-library/reference/realloc.md)