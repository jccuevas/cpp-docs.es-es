---
title: "_fileno | Microsoft Docs"
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
  - "_fileno"
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
  - "_fileno"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "identificadores de archivo [C++], obtener de flujos"
  - "fileno (función)"
  - "_fileno (función)"
  - "flujos, obtener identificadores de archivo"
ms.assetid: 86474174-2f17-4100-bcc4-352dd976c7b5
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fileno
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtener el descriptor de archivo asociado a un flujo  
  
## Sintaxis  
  
```  
int _fileno(   
   FILE *stream   
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura de `FILE`.  
  
## Valor devuelto  
 `_fileno` devuelve descriptor de archivo.  No se devuelve ningún error.  El resultado es indefinido si `stream` no especifica un archivo abierto.  Si la secuencia está `NULL`, \_`fileno` invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, esta función devuelve \-1 y establece `errno` a `EINVAL`.  
  
 Para obtener más información sobre estos y otros códigos error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
> [!NOTE]
>  Si `stdout` o `stderr` no está asociado a una secuencia de salida \(por ejemplo, en una aplicación para Windows sin una ventana de consola\), descriptor de archivo devuelto es \-2.  En versiones anteriores, descriptor de archivo devuelto es \-1.  Este cambio permite a las aplicaciones para diferenciar esta condición de un error.  
  
## Comentarios  
 La rutina de `_fileno` devuelve descriptor de archivo asociado actualmente a `stream`.  Esta rutina se implementa como una función como macro.  Para obtener información sobre cómo elegir cualquier implementación, vea [Elegir las funciones y macros de Entre](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_fileno`|\<stdio.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_fileno.c  
// This program uses _fileno to obtain  
// the file descriptor for some standard C streams.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   printf( "The file descriptor for stdin is %d\n", _fileno( stdin ) );  
   printf( "The file descriptor for stdout is %d\n", _fileno( stdout ) );  
   printf( "The file descriptor for stderr is %d\n", _fileno( stderr ) );  
}  
```  
  
  **Descriptor de archivo para el stdin es 0**  
**Descriptor de archivo para el stdout es 1**  
**Descriptor de archivo para el stderr es 2**   
## Equivalente en .NET Framework  
 [System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [\_fdopen, \_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [\_filelength, \_filelengthi64](../../c-runtime-library/reference/filelength-filelengthi64.md)   
 [fopen, \_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, \_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)