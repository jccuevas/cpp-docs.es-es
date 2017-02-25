---
title: "_CrtIsMemoryBlock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtIsMemoryBlock"
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
apitype: "DLLExport"
f1_keywords: 
  - "CrtlsMemoryBlock"
  - "_CrtIsMemoryBlock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtIsMemoryBlock (función)"
  - "CrtIsMemoryBlock (función)"
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _CrtIsMemoryBlock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Comprueba que un bloque de memoria especificado está en el montón local y que tiene un identificador válido de tipo de bloque del montón de depuración \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
int _CrtIsMemoryBlock(   
   const void *userData,  
   unsigned int size,  
   long *requestNumber,  
   char **filename,  
   int *linenumber   
);  
```  
  
#### Parámetros  
 \[in\] `userData`  
 Puntero al principio del bloque de memoria que se va a comprobar.  
  
 \[in\] `size`  
 Tamaño del bloque especificado, en bytes.  
  
 \[out\] `requestNumber`  
 Puntero al número de asignación del bloque o `NULL`.  
  
 \[out\] `filename`  
 Puntero al nombre del archivo de código fuente que solicitó el bloque o `NULL`.  
  
 \[out\] `linenumber`  
 Puntero al número de línea del archivo de código fuente o `NULL`.  
  
## Valor devuelto  
 `_CrtIsMemoryBlock` devuelve `TRUE`  si el bloque de memoria especificado está en el montón local y tiene un identificador válido de tipo de bloque del montón de depuración; de lo contrario, la función devuelve `FALSE`.  
  
## Comentarios  
 La función `_CrtIsMemoryBlock` comprueba que un bloque de memoria especificado está en el montón local de la aplicación y que tiene un identificador de tipo de bloque válido.  Esta función también se puede usar para obtener el número de orden de la asignación de objetos, y el nombre y el número de línea del archivo de código fuente en el que se solicitó la asignación del bloque de memoria originalmente.  Si se pasan valores no nulos para los parámetros `requestNumber`, `filename` o `linenumber`, `_CrtIsMemoryBlock` establece estos parámetros en los valores del encabezado de depuración del bloque de memoria, si encuentra el bloque en el montón local.  Cuando no se define [\_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtIsMemoryBlock` se quitan durante el preprocesamiento.  
  
 Si `_CrtIsMemoryBlock` produce un error, devuelve `FALSE` y los parámetros de salida se inicializan con los valores predeterminados: `requestNumber` y `lineNumber` se establecen en 0 y `filename` se establece en `NULL`.  
  
 Dado que esta función devuelve `TRUE` o `FALSE`, se puede pasar a una de las macros de [\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) para crear un mecanismo sencillo de control de errores de depuración.  En el ejemplo siguiente se genera un error de aserción si la dirección especificada no se está en el montón local:  
  
```  
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,   
&filename, &linenumber ) );  
```  
  
 Para obtener más información sobre el uso de `_CrtIsMemoryBlock` con otras funciones y macros de depuración, vea [Macros para los informes](../Topic/Macros%20for%20Reporting.md).  Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_CrtIsMemoryBlock`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 Vea el ejemplo del tema [](../../c-runtime-library/reference/crtisvalidheappointer.md "_CrtIsValidHeapPointer").  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)