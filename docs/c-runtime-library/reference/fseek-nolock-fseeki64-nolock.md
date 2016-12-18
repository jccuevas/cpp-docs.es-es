---
title: "_fseek_nolock, _fseeki64_nolock | Microsoft Docs"
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
  - "_fseek_nolock"
  - "_fseeki64_nolock"
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
  - "_fseek_nolock"
  - "_fseeki64_nolock"
  - "fseek_nolock"
  - "fseeki64_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fseek_nolock (función)"
  - "_fseeki64_nolock (función)"
  - "punteros a archivos [C++], mover"
  - "fseek_nolock (función)"
  - "fseeki64_nolock (función)"
  - "buscar punteros a archivos"
ms.assetid: 2dd4022e-b715-462b-b935-837561605a02
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fseek_nolock, _fseeki64_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Mueve el puntero de archivo a una ubicación especificada.  
  
## Sintaxis  
  
```  
int _fseek_nolock(   
   FILE *stream,  
   long offset,  
   int origin   
);  
int _fseeki64_nolock(   
   FILE *stream,  
   __int64 offset,  
   int origin   
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura de `FILE`.  
  
 `offset`  
 Número de bytes de `origin.`  
  
 `origin`  
 Posición inicial.  
  
## Valor devuelto  
 Igual que [fseek, \_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md) respectivamente.  
  
## Comentarios  
 Estas funciones son las versiones de no bloqueo de `fseek` y de `_fseeki64`, respectivamente.          Éstos son idénticos a `fseek` y a `_fseeki64` salvo que no se protegen de interferencia por otros subprocesos.  Estas funciones pueden ser más rápidas porque no provocan en la sobrecarga de bloquear out otros subprocesos.  Use estas funciones solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fseek`|\<stdio.h\>|  
|`_fseeki64`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
  
-   [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
-   [System::IO::FileStream::Seek](https://msdn.microsoft.com/en-us/library/system.io.filestream.seek.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [ftell, \_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [\_lseek, \_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)   
 [rewind](../../c-runtime-library/reference/rewind.md)