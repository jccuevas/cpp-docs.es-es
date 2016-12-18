---
title: "_ftell_nolock, _ftelli64_nolock | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ftelli64_nolock"
  - "_ftell_nolock"
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
  - "_ftelli64_nolock"
  - "ftelli64_nolock"
  - "ftell_nolock"
  - "_ftell_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftell_nolock (función)"
  - "_ftelli64_nolock (función)"
  - "punteros a archivos [C++], obtener posición actual"
  - "ftell_nolock (función)"
  - "ftelli64_nolock (función)"
ms.assetid: 84e68b0a-32f8-4c4a-90ad-3f2387685ede
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ftell_nolock, _ftelli64_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene la posición actual de un puntero de archivo, sin bloquear el subproceso.  
  
## Sintaxis  
  
```  
long _ftell_nolock(   
   FILE *stream   
);  
__int64 _ftelli64_nolock(   
   FILE *stream   
);  
```  
  
#### Parámetros  
 `stream`  
 Destino la estructura de `FILE` .  
  
## Valor devuelto  
 Igual que `ftell` y `_ftelli64`.  Para obtener más información, vea [ftell, \_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)**.**  
  
## Comentarios  
 Estas funciones son versiones de no bloqueo de `ftell` y de `_ftelli64`, respectivamente.  Son idénticas a `ftell` y a `_ftelli64`salvo que no se protegen de interferencia por otros subprocesos.  Estas funciones pueden ser más rápidas porque no provocan en la sobrecarga de bloquear out otros subprocesos.  Use estas funciones solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.  
  
## Requisitos  
  
|Función|Encabezado necesario|Encabezado opcional|  
|-------------|--------------------------|-------------------------|  
|`ftell_nolock`|\<stdio.h\>|\<errno.h\>|  
|`_ftelli64_nolock`|\<stdio.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)   
 [fseek, \_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)   
 [\_lseek, \_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)   
 [ftell, \_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)