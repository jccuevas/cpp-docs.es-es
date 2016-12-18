---
title: "_fwrite_nolock | Microsoft Docs"
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
  - "_fwrite_nolock"
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
  - "_fwrite_nolock"
  - "fwrite_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fwrite_nolock (función)"
  - "fwrite_nolock (función)"
  - "secuencias, escribir datos en"
ms.assetid: 2b4ec6ce-742e-4615-8407-44a0a18ec1d7
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fwrite_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe datos en una secuencia, sin bloquear el subproceso.  
  
## Sintaxis  
  
```  
size_t _fwrite_nolock(  
   const void *buffer,  
   size_t size,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### Parámetros  
 `buffer`  
 Puntero a escribir los datos.  
  
 `size`  
 Tamaño del elemento en bytes.  
  
 `count`  
 Número máximo de elementos que se deben escribir.  
  
 `stream`  
 Puntero a la estructura de `FILE`.  
  
## Valor devuelto  
 Igual que [fwrite](../../c-runtime-library/reference/fwrite.md).  
  
## Comentarios  
 Esta función es una versión de no bloqueo de `fwrite`.  Es idéntica a `fwrite` salvo que no se protege de interferencia por otros subprocesos.  Puede ser más rápida porque no incurre en la sobrecarga de bloquear out otros subprocesos.  Utilice esta función solo en contextos seguros como aplicaciones de un único subproceso o donde los identificadores de ámbito de llamada subproceso ya el aislamiento.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_fwrite_nolock`|\<stdio.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo para [fread](../../c-runtime-library/reference/fread.md).  
  
## Equivalente en .NET Framework  
 [System::IO::FileStream::Write](https://msdn.microsoft.com/en-us/library/system.io.filestream.write.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fread](../../c-runtime-library/reference/fread.md)   
 [\_write](../../c-runtime-library/reference/write.md)