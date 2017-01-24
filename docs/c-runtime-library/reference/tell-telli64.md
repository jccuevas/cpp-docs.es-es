---
title: "_tell, _telli64 | Microsoft Docs"
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
  - "_telli64"
  - "_tell"
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
  - "tell"
  - "telli64"
  - "_telli64"
  - "_tell"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tell (función)"
  - "_telli64 (función)"
  - "punteros a archivos [C++]"
  - "punteros a archivos [C++], obtener"
  - "tell (función)"
  - "telli64 (función)"
ms.assetid: 1500e8f9-8fec-4253-9eec-ec66125dfc9b
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _tell, _telli64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtenga la posición del puntero de archivo.  
  
## Sintaxis  
  
```  
long _tell(  
   int handle  
);  
__int64 _telli64(  
   int handle   
);  
```  
  
#### Parámetros  
 `handle`  
 Descriptor de archivo que hace referencia al archivo abierto.  
  
## Valor devuelto  
 La posición actual del puntero de archivo.  En los dispositivos incapaces de búsqueda, el valor devuelto es indefinido.  
  
 Un valor devuelto de – 1L indica un error.  Si `handle` es descriptor de archivo no válido, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, este `errno` establecido funciones a `EBADF` y retorno \-1L.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre este y otros códigos de retorno.  
  
## Comentarios  
 La función de `_tell` obtiene la posición actual del puntero de archivo \(si existe\) asociado al argumento de `handle` .  La posición se expresa como número de bytes desde el principio del archivo.  Para la función de `_telli64` , este valor se expresa como un entero de 64 bits.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_tell`, `_telli64`|\<io.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_tell.c  
// This program uses _tell to tell the  
// file pointer position after a file read.  
//  
  
#include <io.h>  
#include <stdio.h>  
#include <fcntl.h>  
#include <share.h>  
#include <string.h>  
  
int main( void )  
{  
   int  fh;  
   char buffer[500];  
  
   if ( _sopen_s( &fh, "crt_tell.txt", _O_RDONLY, _SH_DENYNO, 0) )  
   {  
      char buff[50];  
      _strerror_s( buff, sizeof(buff), NULL );  
      printf( buff );  
      exit( -1 );  
   }  
  
   if( _read( fh, buffer, 500 ) > 0 )  
      printf( "Current file position is: %d\n", _tell( fh ) );  
   _close( fh );  
}  
```  
  
## Entrada: crt\_tell.txt  
  
```  
Line one.  
Line two.  
```  
  
### Resultados  
  
```  
Current file position is: 20  
```  
  
## Vea también  
 [E\/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [ftell, \_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [\_lseek, \_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)