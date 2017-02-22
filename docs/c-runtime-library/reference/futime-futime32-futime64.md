---
title: "_futime, _futime32, _futime64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_futime64"
  - "_futime32"
  - "_futime"
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
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "futime"
  - "_futime"
  - "futime64"
  - "_futime64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_futime (función)"
  - "futime32 (función)"
  - "futime64 (función)"
  - "hora de modificación de archivo [C++]"
  - "_futime64 (función)"
  - "futime (función)"
  - "_futime32 (función)"
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# _futime, _futime32, _futime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el tiempo de modificación en un archivo abierto.  
  
## Sintaxis  
  
```  
int _futime(   
   int fd,  
   struct _utimbuf *filetime   
);  
int _futime32(   
   int fd,  
   struct __utimbuf32 *filetime   
);  
int _futime64(   
   int fd,  
   struct __utimbuf64 *filetime   
);  
```  
  
#### Parámetros  
 `fd`  
 Descriptor de archivo al archivo abierto.  
  
 `filetime`  
 Puntero a la estructura que contiene la nueva fecha de modificación.  
  
## Valor devuelto  
 Return 0 si correctamente.  Si se produce un error, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve – 1 y `errno` se establece en `EBADF`, indicando descriptor de archivo no válido, o a `EINVAL`, que indica un parámetro no válido.  
  
## Comentarios  
 La rutina de `_futime` establece la fecha de modificación y tiempo de acceso en el archivo abierto asociado a *`fd`.* `_futime` es idéntico a [\_utime](../../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md), excepto en que el argumento es descriptor de archivo de un archivo abierto, en lugar del nombre de un archivo o una ruta de acceso a un archivo.  La estructura de `_utimbuf` contiene los campos por la nueva fecha y hora de acceso de modificación.  Ambos campos deben contener valores válidos.  `_utimbuf32` y `_utimbuf64` son idénticos a `_utimbuf` a excepción de los tipos de 32 bits y 64 bits del tiempo, respectivamente.  `_futime` y `_utimbuf` utilizan un tipo de 64 bits del tiempo y `_futime` es idéntico en comportamiento a `_futime64`.  Si necesita forzar el comportamiento antiguo, defina `_USE_32BIT_TIME_T`.  Ello hace `_futime` para ser idéntico en comportamiento a `_futime32` y hace que la estructura de `_utimbuf` para utilizar el tipo de 32 bits del tiempo, lo que equivale a `__utimbuf32`.  
  
 `_futime64`, que utiliza la estructura de `__utimbuf64` , puede leer y modificar las fechas del archivo con 23:59: 59, el 31 de diciembre, 3000, hora UTC; mientras que falla una llamada a `_futime32` si la fecha del archivo es posterior que 19:14: 7 de enero de 18, 2038, La hora UTC.  La medianoche, el 1 de enero de 1970, es el límite inferior del intervalo de fechas para estas funciones.  
  
## Requisitos  
  
|Función|Encabezado necesario|Encabezado opcional|  
|-------------|--------------------------|-------------------------|  
|`_futime`|\<sistema\/utime.h\>|\<errno.h\>|  
|`_futime32`|\<sistema\/utime.h\>|\<errno.h\>|  
|`_futime64`|\<sistema\/utime.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_futime.c  
// This program uses _futime to set the  
// file-modification time to the current time.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <fcntl.h>  
#include <io.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <sys/utime.h>  
#include <share.h>  
  
int main( void )  
{  
   int hFile;  
  
   // Show file time before and after.   
   system( "dir crt_futime.c_input" );  
  
   _sopen_s( &hFile, "crt_futime.c_input", _O_RDWR, _SH_DENYNO, 0 );  
  
   if( _futime( hFile, NULL ) == -1 )  
      perror( "_futime failed\n" );  
   else  
      printf( "File time modified\n" );  
  
   _close (hFile);  
  
   system( "dir crt_futime.c_input" );  
}  
```  
  
## Entrada: crt\_futime.c\_input  
  
```  
Arbitrary file contents.  
```  
  
### Resultados del ejemplo  
  
```  
Volume in drive Z has no label.  
 Volume Serial Number is 5C68-57C1  
  
 Directory of Z:\crt  
  
03/25/2004  10:40 AM                24 crt_futime.c_input  
               1 File(s)             24 bytes  
               0 Dir(s)  24,268,476,416 bytes free  
 Volume in drive Z has no label.  
 Volume Serial Number is 5C68-57C1  
  
 Directory of Z:\crt  
  
03/25/2004  10:41 AM                24 crt_futime.c_input  
               1 File(s)             24 bytes  
               0 Dir(s)  24,268,476,416 bytes free  
File time modified  
```  
  
## Equivalente en .NET Framework  
  
-   [System::IO::File::SetLastAccessTime](https://msdn.microsoft.com/en-us/library/system.io.file.setlastaccesstime.aspx)  
  
-   [System::IO::File::SetLastWriteTime](https://msdn.microsoft.com/en-us/library/system.io.file.setlastwritetime.aspx)  
  
-   [System::IO::File::SetCreationTime](https://msdn.microsoft.com/en-us/library/system.io.file.setcreationtime.aspx)  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)