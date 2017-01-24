---
title: "_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fstat32"
  - "_fstat64"
  - "_fstati64"
  - "_fstat"
  - "_fstat64i32"
  - "_fstat32i64"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_fstat32i64"
  - "fstat"
  - "fstat64i32"
  - "_fstat64"
  - "_fstati64"
  - "fstat64"
  - "_fstat32"
  - "fstat32i64"
  - "fstati64"
  - "_fstat"
  - "fstat32"
  - "_fstat64i32"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fstat64 (función)"
  - "fstati64 (función)"
  - "_fstat64i32 (función)"
  - "_fstat32i64 (función)"
  - "_fstat32 (función)"
  - "información de archivo"
  - "fstat64i32 (función)"
  - "fstat32 (función)"
  - "fstat (función)"
  - "fstat64 (función)"
  - "_fstat (función)"
  - "_fstati64 (función)"
  - "fstat32i64 (función)"
ms.assetid: 088f5e7a-9636-4cf7-ab8e-e28d2aa4280a
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene información sobre un archivo abierto.  
  
## Sintaxis  
  
```  
int _fstat(   
   int fd,  
   struct _stat *buffer   
);  
int _fstat32(   
   int fd,  
   struct __stat32 *buffer   
);  
int _fstat64(   
   int fd,  
   struct __stat64 *buffer   
);  
int _fstati64(   
   int fd,  
   struct _stati64 *buffer   
);  
int _fstat32i64(   
   int fd,  
   struct _stat32i64 *buffer   
);  
int _fstat64i32(   
   int fd,  
   struct _stat64i32 *buffer   
);  
```  
  
#### Parámetros  
 `fd`  
 Descriptor del archivo abierto.  
  
 `buffer`  
 Puntero a la estructura para almacenar los resultados.  
  
## Valor devuelto  
 Devuelve 0 si se obtiene la información de estado de archivo. Un valor devuelto de –1 indica un error. Si el descriptor de archivo no es válido o `buffer` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EBADF`, en el caso de un descriptor de archivo no válido o a `EINVAL`, Si `buffer` es `NULL`.  
  
## Comentarios  
 El `_fstat` función obtiene información acerca del archivo abierto asociado `fd` y lo almacena en la estructura que señala `buffer`. El `_stat` estructura, definida en sys\\stat, contiene los siguientes campos.  
  
 `st_atime`  
 Hora del último acceso de archivo.  
  
 `st_ctime`  
 Hora de creación del archivo.  
  
 `st_dev`  
 Si un dispositivo `fd`; de lo contrario, 0.  
  
 `st_mode`  
 Máscara de bits para información de modo de archivo. El `_S_IFCHR` bit se establece si `fd` hace referencia a un dispositivo. El `_S_IFREG` bit se establece si `fd` hace referencia a un archivo normal. Los bits de lectura y escritura se establecen según el modo de permiso del archivo.`_S_IFCHR` y otras constantes se definen en sys\\stat.  
  
 `st_mtime`  
 Hora de la última modificación del archivo.  
  
 `st_nlink`  
 Siempre 1 en sistemas de archivos que no son NTFS.  
  
 `st_rdev`  
 Si un dispositivo `fd`; de lo contrario, 0.  
  
 `st_size`  
 Tamaño del archivo en bytes.  
  
 Si `fd` hace referencia a un dispositivo, el `st_atime`, `st_ctime`, `st_mtime`, y `st_size` campos no son significativos.  
  
 Dado que utiliza Stat.h el [\_dev\_t](../../c-runtime-library/standard-types.md) escriba, que se define en Types.h, debe incluir Types.h antes de Stat.h en el código.  
  
 `_fstat64`, que utiliza el `__stat64` estructura, permite expresar de hasta 23:59:59, hasta el 31 de diciembre de 3000, UTC; las fechas de creación del archivo, mientras que las demás funciones solo representan fechas hasta las 23:59:59 del 18 de enero de 2038, hora UTC. La noche del 1 de enero de 1970, es el límite inferior del intervalo de fechas para todas estas funciones.  
  
 Variaciones de estas funciones admiten tipos en tiempo de 32 bits o 64 bits y longitudes de archivos de 32 bits o 64 bits. El primer sufijo numérico \(`32` o `64`\) indica el tamaño del tipo de tiempo usado; el segundo sufijo es `i32` o `i64`, lo que indica si el tamaño del archivo se representa como un entero de 32 o 64 bits.  
  
 `_fstat` es equivalente a `_fstat64i32`, y `struct``_stat` contiene una hora de 64 bits. Esto es así a menos que `_USE_32BIT_TIME_T` se define, en cuyo caso el comportamiento anterior está en vigor; `_fstat` usa uno de 32 bits, y `struct``_stat` contiene una hora de 32 bits. Lo mismo puede decirse de `_fstati64`.  
  
### Tipo de tiempo y variaciones de tipo de longitud de archivo de \_stat  
  
|Funciones|¿\_USE\_32BIT\_TIME\_T definida?|Tipo de tiempo|Tipo de longitud de archivo|  
|---------------|--------------------------------------|--------------------|---------------------------------|  
|`_fstat`|No definida|64 bits|32 bits|  
|`_fstat`|Definido|32 bits|32 bits|  
|`_fstat32`|No se ve afectada por la definición de macro|32 bits|32 bits|  
|`_fstat64`|No se ve afectada por la definición de macro|64 bits|64 bits|  
|`_fstati64`|No definida|64 bits|64 bits|  
|`_fstati64`|Definido|32 bits|64 bits|  
|`_fstat32i64`|No se ve afectada por la definición de macro|32 bits|64 bits|  
|`_fstat64i32`|No se ve afectada por la definición de macro|64 bits|32 bits|  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_fstat`|\< sys\/STAT.h \> y \< sys\/types.h \>|  
|`_fstat32`|\< sys\/STAT.h \> y \< sys\/types.h \>|  
|`_fstat64`|\< sys\/STAT.h \> y \< sys\/types.h \>|  
|`_fstati64`|\< sys\/STAT.h \> y \< sys\/types.h \>|  
|`_fstat32i64`|\< sys\/STAT.h \> y \< sys\/types.h \>|  
|`_fstat64i32`|\< sys\/STAT.h \> y \< sys\/types.h \>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_fstat.c  
// This program uses _fstat to report  
// the size of a file named F_STAT.OUT.  
  
#include <io.h>  
#include <fcntl.h>  
#include <time.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <errno.h>  
#include <share.h>  
  
int main( void )  
{  
   struct _stat buf;  
   int fd, result;  
   char buffer[] = "A line to output";  
   char timebuf[26];  
   errno_t err;  
  
   _sopen_s( &fd,  
             "f_stat.out",  
             _O_CREAT | _O_WRONLY | _O_TRUNC,  
             _SH_DENYNO,  
             _S_IREAD | _S_IWRITE );  
   if( fd != -1 )  
      _write( fd, buffer, strlen( buffer ) );  
  
   // Get data associated with "fd":   
   result = _fstat( fd, &buf );  
  
   // Check if statistics are valid:   
   if( result != 0 )  
   {  
      if (errno == EBADF)  
        printf( "Bad file descriptor.\n" );  
      else if (errno == EINVAL)  
        printf( "Invalid argument to _fstat.\n" );  
   }  
   else  
   {  
      printf( "File size     : %ld\n", buf.st_size );  
      err = ctime_s(timebuf, 26, &buf.st_mtime);  
      if (err)  
      {  
         printf("Invalid argument to ctime_s.");  
         exit(1);  
      }  
      printf( "Time modified : %s", timebuf );  
   }  
   _close( fd );  
}  
```  
  
```Output  
Tamaño de archivo: modificación 16: 07 de mayo del miércoles 15:25:11 2003  
```  
  
## Equivalente en .NET Framework  
 No disponible. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_access, \_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [\_chmod, \_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_filelength, \_filelengthi64](../../c-runtime-library/reference/filelength-filelengthi64.md)   
 [\_stat, \_wstat \(Funciones\)](../../c-runtime-library/reference/stat-functions.md)