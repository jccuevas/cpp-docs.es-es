---
title: "_chsize_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_chsize_s"
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
  - "chsize_s"
  - "_chsize_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_chsize_s (función)"
  - "chsize_s (función)"
  - "archivos [C++], cambiar el tamaño"
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _chsize_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cambia el tamaño de un archivo.  Ésta es una versión de [\_chsize](../../c-runtime-library/reference/chsize.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t _chsize_s(   
   int fd,  
   __int64 size   
);  
```  
  
#### Parámetros  
 `fd`  
 Descriptor de archivo que hace referencia a un archivo abierto.  
  
 `size`  
 Nueva longitud en bytes de un archivo.  
  
## Valor devuelto  
 `_chsize_s` devuelve el valor 0 si el tamaño de archivo cambia correctamente.  Devuelve un valor distinto de cero indica un error: el valor devuelto es `EACCES` si el archivo especificado está bloqueado y el acceso, `EBADF` si el archivo especificado es de solo lectura o descriptor es no válido, `ENOSPC` si no se permite ningún espacio en el dispositivo, o `EINVAL` si el tamaño es menor que cero.  `errno` está establecida en el mismo valor.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función de `_chsize_s` extiende o trunca el archivo asociado a `fd` con la longitud especificada por `size`.  El archivo debe estar abierto en un modo que permite escribir.  Se agregan caracteres null \(“\\0”\) si se mejora el archivo.  Si se trunca el archivo, todos los datos del final del archivo abreviado a la longitud original del archivo se pierde.  
  
 `_chsize_s` toma un entero de 64 bits como el tamaño de archivo, por lo que puede controlar los tamaños de archivo mayor de 4 GB.  `_chsize` se limita a los tamaños de archivo de 32 bits.  
  
 Esta función valida sus parámetros.  Si `fd` no es descriptor de archivo válido o el tamaño es menor que cero, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_chsize_s`|\<io.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
  
-   [System::IO::Stream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.stream.setlength.aspx)  
  
-   [System::IO::FileStream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.filestream.setlength.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_chsize](../../c-runtime-library/reference/chsize.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_creat, \_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)