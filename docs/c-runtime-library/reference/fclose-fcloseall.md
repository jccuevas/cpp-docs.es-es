---
title: "fclose, _fcloseall | Microsoft Docs"
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
  - "fclose"
  - "_fcloseall"
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
  - "fclose"
  - "_fcloseall"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "fclose (función)"
  - "flujos, cierre"
  - "_fcloseall (función)"
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fclose, _fcloseall
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cierra una secuencia \(`fclose`\) o cierre las secuencias todo abierto \(`_fcloseall`\).  
  
## Sintaxis  
  
```  
int fclose(   
   FILE *stream   
);  
int _fcloseall( void );  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura `FILE`.  
  
## Valor devuelto  
 `fclose` devuelve 0 si se cierra la secuencia correctamente.  `_fcloseall` devuelve el número total de secuencias se cierra.  Ambas funciones `EOF` return para indicar un error.  
  
## Comentarios  
 La función de `fclose` cierra `stream`.  Si `stream` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `fclose` establece `errno` a `EINVAL` y devuelve `EOF`.  Se recomienda que el puntero de `stream` garantiza que siempre antes de llamar a esta función.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.  
  
 La función de `_fcloseall` cierre las secuencias todo abierto excepto `stdin`, `stdout`, `stderr` \(y, en MS\-DOS, `_stdaux` y `_stdprn`\).  También se cierra y se elimina cualquier archivo temporal creado por `tmpfile`.  En ambas funciones, todos los búferes asociados a la secuencia se vacía antes de cerrar.  Se liberan los búferes Sistema\- asignados cuando se cierra la secuencia.  Los búferes asignados por el usuario con `setbuf` y `setvbuf` automáticamente no se libera.  
  
 **Note:** Cuando estas funciones se utiliza para cerrar una secuencia, descriptor de archivo subyacente y el identificador de archivos de sistema operativo \(o el socket\) están cerrados, así como la secuencia.  Así, si se ha abierto el archivo como un identificador de archivos o descriptor de archivo y cerrar originalmente con `fclose`, tampoco llame a `_close` para cerrar descriptor de archivo; no llame a la función `CloseHandle` Win32 para cerrar el identificador de archivos.  
  
 `fclose` y `_fcloseall` incluyen código para protegerse contra interfieran otros subprocesos.  Para la versión de no bloqueo de `fclose`, vea `_fclose_nolock`.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fclose`|\<stdio.h\>|  
|`_fcloseall`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo para [fopen](../../c-runtime-library/reference/fopen-wfopen.md).  
  
## Equivalente en .NET Framework  
  
-   [System::IO::BinaryReader::Close](https://msdn.microsoft.com/en-us/library/system.io.binaryreader.close.aspx)  
  
-   [System::IO::BinaryWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.binarywriter.close.aspx)  
  
-   [System::IO::StringReader::Close](https://msdn.microsoft.com/en-us/library/system.io.stringreader.close.aspx)  
  
-   [System::IO::StringWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.stringwriter.close.aspx)  
  
-   [System::IO::Stream::Close](https://msdn.microsoft.com/en-us/library/system.io.stream.close.aspx)  
  
-   [System::IO::StreamReader::Close](https://msdn.microsoft.com/en-us/library/system.io.streamreader.close.aspx)  
  
-   [System::IO::StreamWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.close.aspx)  
  
-   [System::IO::TextReader::Close](https://msdn.microsoft.com/en-us/library/system.io.textreader.close.aspx)  
  
-   [System::IO::TextWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.textwriter.close.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_fdopen, \_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen, \_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, \_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)