---
title: "_rmtmp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_rmtmp"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "rmtmp"
  - "_rmtmp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_rmtmp (función)"
  - "archivos [C++], quitar"
  - "archivos [C++], temporal"
  - "quitar archivos temporales"
  - "rmtmp (función)"
  - "archivos temporales [C++], quitar"
ms.assetid: 7419501e-2587-4f2a-b469-0dca07f84736
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# _rmtmp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Quita los archivos temporales.  
  
## Sintaxis  
  
```  
  
int _rmtmp( void );  
```  
  
## Valor devuelto  
 `_rmtmp` devuelve el número de archivos temporales se cierra y eliminado.  
  
## Comentarios  
 La función de `_rmtmp` limpia todos los archivos temporales en el directorio actual.  La función quita sólo los archivos creados por `tmpfile`; utilice solo en el mismo directorio que los archivos temporales creados.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_rmtmp`|\<stdio.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 Vea el ejemplo para [tmpfile](../../c-runtime-library/reference/tmpfile.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [\_flushall](../../c-runtime-library/reference/flushall.md)   
 [tmpfile](../../c-runtime-library/reference/tmpfile.md)   
 [\_tempnam, \_wtempnam, tmpnam, \_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)