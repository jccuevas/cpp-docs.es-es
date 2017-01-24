---
title: "_flushall | Microsoft Docs"
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
  - "_flushall"
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
  - "_flushall"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "flushall (función)"
  - "vaciar secuencias"
  - "flujos, vaciar"
  - "_flushall (función)"
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _flushall
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Vacía todos los flujos y borra todos los búferes.  
  
## Sintaxis  
  
```  
int _flushall( void );  
```  
  
## Valor devuelto  
 `_flushall` devuelve el número de flujos abiertos \(entrada y salida\).  No se devuelve ningún error.  
  
## Comentarios  
 De forma predeterminada, la función `_flushall` escribe en los archivos correspondientes el contenido de todos los búferes asociados a los flujos de salida abiertos.  Se borra el contenido actual de todos los búferes asociados a los flujos de entrada abiertos. Normalmente, el sistema operativo mantiene estos búferes y determina el momento óptimo para escribir los datos automáticamente en el disco: cuando el búfer está lleno, cuando se cierra un flujo o cuando un programa finaliza con normalidad sin cerrar flujos.  
  
 Si una lectura sigue a una llamada a `_flushall`, se insertan más datos de los archivos de entrada en los búferes.  Todos los flujos permanecen abiertos después de la llamada a `_flushall`.  
  
 La característica de confirmación en disco de la biblioteca en tiempo de ejecución permite asegurarse de que los datos críticos se escribe directamente en el disco y no en los búferes del sistema operativo.  Sin tener que volver a escribir un programa existente, puede habilitar esta característica vinculando los archivos objeto del programa a Commode.obj.  En el archivo ejecutable resultante, las llamadas a `_flushall` escriben el contenido de todos los búferes en el disco.  Commode.obj solo afecta a `_flushall` y `fflush`.  
  
 Para obtener información sobre cómo controlar la característica de confirmación en disco, vea [E\/S de flujos](../../c-runtime-library/stream-i-o.md), [fopen](../../c-runtime-library/reference/fopen-wfopen.md) y [\_fdopen](../../c-runtime-library/reference/fdopen-wfdopen.md).  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_flushall`|\<stdio.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_flushall.c  
// This program uses _flushall  
// to flush all open buffers.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int numflushed;  
  
   numflushed = _flushall();  
   printf( "There were %d streams flushed\n", numflushed );  
}  
```  
  
  **Se vaciaron 3 flujos**   
## Equivalente en .NET Framework  
  
-   [System::IO::FileStream::Flush](https://msdn.microsoft.com/en-us/library/2bw4h516.aspx)  
  
-   [System::IO::StreamWriter::Flush](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.flush.aspx)  
  
-   [System::IO::TextWriter::Flush](https://msdn.microsoft.com/en-us/library/system.io.textwriter.flush.aspx)  
  
-   [System::IO::BinaryWriter::Flush](https://msdn.microsoft.com/en-us/library/system.io.binarywriter.flush.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [\_commit](../../c-runtime-library/reference/commit.md)   
 [fclose, \_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)