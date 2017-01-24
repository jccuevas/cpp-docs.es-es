---
title: "_filelength, _filelengthi64 | Microsoft Docs"
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
  - "_filelengthi64"
  - "_filelength"
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
  - "_filelength"
  - "_filelengthi64"
  - "filelengthi64"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_filelength (función)"
  - "_filelengthi64 (función)"
  - "filelength (función)"
  - "filelengthi64 (función)"
  - "archivos [C++], longitud"
  - "longitudes, archivo"
ms.assetid: 3ab83d5a-543c-4079-b9d9-0abfc7da0275
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _filelength, _filelengthi64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene la longitud de un archivo.  
  
## Sintaxis  
  
```  
long _filelength(   
   int fd   
);  
__int64 _filelengthi64(   
   int fd   
);  
```  
  
#### Parámetros  
 `fd`  
 Destino descriptor de archivo.  
  
## Valor devuelto  
 `_filelength` y `_filelengthi64` devuelven la longitud del archivo, en bytes, del archivo de destino asociado a `fd`.  Si `fd` es descriptor de archivo no válido, esta función invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, ambas funciones devuelven – 1L para indicar un error y un conjunto `errno` a `EBADF`.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_filelength`|\<io.h\>|  
|`_filelengthi64`|\<io.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo para [\_chsize](../../c-runtime-library/reference/chsize.md).  
  
## Equivalente en .NET Framework  
  
-   [System::IO::Stream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.stream.setlength.aspx)  
  
-   [System::IO::FileStream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.filestream.setlength.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_chsize](../../c-runtime-library/reference/chsize.md)   
 [\_fileno](../../c-runtime-library/reference/fileno.md)   
 [\_fstat, \_fstat32, \_fstat64, \_fstati64, \_fstat32i64, \_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_fstat, \_fstat32, \_fstat64, \_fstati64, \_fstat32i64, \_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_stat, \_wstat \(Funciones\)](../../c-runtime-library/reference/stat-functions.md)   
 [\_stat, \_wstat \(Funciones\)](../../c-runtime-library/reference/stat-functions.md)