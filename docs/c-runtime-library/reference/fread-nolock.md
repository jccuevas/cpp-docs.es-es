---
title: "_fread_nolock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fread_nolock"
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
  - "_fread_nolock"
  - "fread_nolock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fread_nolock (función)"
  - "datos [C++], leer en secuencia de entrada"
  - "fread_nolock (función)"
  - "leer datos [C++], en secuencias de entrada"
  - "secuencias [C++], leer datos de"
ms.assetid: 60e4958b-1097-46f5-a77b-94af5e7dba40
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _fread_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee los datos de una secuencia, sin bloquearse otros subprocesos.  
  
## Sintaxis  
  
```  
size_t _fread_nolock(   
   void *buffer,  
   size_t size,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### Parámetros  
 `buffer`  
 Ubicación de almacenamiento de los datos.  
  
 `size`  
 Tamaño del elemento en bytes.  
  
 `count`  
 Número máximo de elementos que se va a leer.  
  
 `stream`  
 Puntero a la estructura de `FILE`.  
  
## Valor devuelto  
 Vea [fread](../../c-runtime-library/reference/fread.md).  
  
## Comentarios  
 Esta función es una versión de no bloqueo de `fread`.  Es idéntica a `fread` salvo que no se protege de interferencia por otros subprocesos.  Puede ser más rápida porque no incurre en la sobrecarga de bloquear out otros subprocesos.  Utilice esta función solo en contextos seguros como aplicaciones de un único subproceso o donde los identificadores de ámbito de llamada subproceso ya el aislamiento.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_fread_nolock`|\<stdio.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 [System::IO::FileStream::Read](https://msdn.microsoft.com/en-us/library/system.io.filestream.read.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [\_read](../../c-runtime-library/reference/read.md)