---
title: "_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_utime64"
  - "_utime"
  - "_wutime"
  - "_wutime64"
  - "_wutime32"
  - "_utime32"
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
  - "_tutime"
  - "_utime64"
  - "wutime"
  - "utime32"
  - "wutime64"
  - "_utime"
  - "wutime32"
  - "_wutime"
  - "utime"
  - "utime64"
  - "_wutime64"
  - "_utime32"
  - "_tutime64"
  - "_wutime32"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "tutime (función)"
  - "utime32 (función)"
  - "utime64 (función)"
  - "_utime (función)"
  - "_tutime32 (función)"
  - "hora [C++], modificación de archivos"
  - "wutime (función)"
  - "_wutime (función)"
  - "_wutime32 (función)"
  - "_tutime64 (función)"
  - "_tutime (función)"
  - "archivos [C++], hora de modificación"
  - "_wutime64 (función)"
  - "_utime32 (función)"
  - "utime (función)"
  - "_utime64 (función)"
  - "wutime64 (función)"
  - "wutime32 (función)"
  - "tutime64 (función)"
  - "tutime32 (función)"
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _utime, _utime32, _utime64, _wutime, _wutime32, _wutime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establezca la hora de modificación del archivo.  
  
## Sintaxis  
  
```  
int _utime(  
   const char *filename,  
   struct _utimbuf *times   
);  
int _utime32(  
   const char *filename,  
   struct __utimbuf32 *times   
);  
int _utime64(  
   const char *filename,  
   struct __utimbuf64 *times   
);  
int _wutime(  
   const wchar_t *filename,  
   struct _utimbuf *times   
);  
int _wutime32(  
   const wchar_t *filename,  
   struct __utimbuf32 *times   
);  
int _wutime64(  
   const wchar_t *filename,  
   struct __utimbuf64 *times   
);  
```  
  
#### Parámetros  
 `filename`  
 Puntero a una cadena que contiene la ruta de acceso o nombre de archivo.  
  
 `times`  
 Puntero a los valores de hora almacenada.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve 0 si se cambia la hora de modificación del archivo. Un valor devuelto de –1 indica un error. Si se pasa un parámetro no válido, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven \-1 y `errno` se establece en uno de los siguientes valores:  
  
 `EACCES`  
 Ruta de acceso especifica el directorio o archivo de sólo lectura  
  
 `EINVAL`  
 No válido `times` argumento  
  
 `EMFILE`  
 Hay demasiados archivos abiertos \(se debe abrir el archivo para cambiar la hora de modificación\)  
  
 `ENOENT`  
 Ruta de acceso o nombre de archivo no encontrado  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.  
  
 La fecha se puede cambiar para un archivo si la fecha de cambio es después de la medianoche del 1 de enero de 1970 y antes de la fecha de finalización de la función utilizada.`_utime` y `_wutime` usar un valor de tiempo de 64 bits, por lo que la fecha de finalización es 23:59:59 del 31 de diciembre de 3000, UTC. Si `_USE_32BIT_TIME_T` se define para forzar el comportamiento anterior, la fecha de finalización es 23:59:59 del 18 de enero de 2038, hora UTC.`_utime32` o `_wutime32` utilizar un tipo en tiempo de 32 bits independientemente de si `_USE_32BIT_TIME_T` se define y siempre tienen la fecha de finalización anterior.`_utime64` o `_wutime64` utilizar siempre el tipo en tiempo de 64 bits, por lo que siempre, estas funciones admiten la fecha de finalización posterior.  
  
## Comentarios  
 El `_utime` función establece la hora de modificación para el archivo especificado por `filename`*.* El proceso debe tener acceso de escritura al archivo para cambiar la hora. En el sistema operativo Windows, puede cambiar el tiempo de acceso y la hora de modificación en el `_utimbuf` estructura. Si `times` es un `NULL` puntero, la hora de modificación se establece en la hora local actual. De lo contrario, `times` debe apuntar a una estructura de tipo `_utimbuf`, definida en SYS\\UTIME. H.  
  
 El `_utimbuf` estructura almacena los tiempos de acceso y modificación de archivos utilizados por `_utime` para cambiar las fechas de modificación del archivo. La estructura tiene los siguientes campos, que son de tipo `time_t`:  
  
 `actime`  
 Tiempo de acceso a archivos  
  
 `modtime`  
 Hora de modificación del archivo  
  
 Las versiones específicas de la `_utimbuf` estructura \(`_utimebuf32` y `__utimbuf64`\) se definen mediante las versiones de 32 bits y 64 bits del tipo de tiempo. Se utilizan en las versiones concretas de 32 bits y 64 bits de esta función.`_utimbuf` de forma predeterminada utiliza un tipo en tiempo de 64 bits a menos que `_USE_32BIT_TIME_T` se define.  
  
 `_utime` es idéntico a `_futime` excepto en que el `filename` argumento de `_utime` es un nombre de archivo o una ruta de acceso a un archivo, en lugar de un descriptor de archivo de un archivo abierto.  
  
 `_wutime` es una versión con caracteres anchos de `_utime`; el argumento `filename` para `_wutime` es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tutime`|`_utime`|`_utime`|`_wutime`|  
|`_tutime32`|`_utime32`|`_utime32`|`_wutime32`|  
|`_tutime64`|`_utime64`|`_utime64`|`_wutime64`|  
  
## Requisitos  
  
|Rutina|Encabezados obligatorios|Encabezados opcionales|  
|------------|------------------------------|----------------------------|  
|`_utime`, `_utime32`, `_utime64`|\< sys\/utime.h \>|\<errno.h\>|  
|`_utime64`|\< sys\/utime.h \>|\<errno.h\>|  
|`_wutime`|\< utime.h \> o \< wchar.h \>|\<errno.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Este programa utiliza `_utime` para establecer la hora de modificación del archivo a la hora actual.  
  
```  
// crt_utime.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <sys/types.h>  
#include <sys/utime.h>  
#include <time.h>  
  
int main( void )  
{  
   struct tm tma = {0}, tmm = {0};  
   struct _utimbuf ut;  
  
   // Fill out the accessed time structure  
   tma.tm_hour = 12;  
   tma.tm_isdst = 0;  
   tma.tm_mday = 15;  
   tma.tm_min = 0;  
   tma.tm_mon = 0;  
   tma.tm_sec = 0;  
   tma.tm_year = 103;  
  
   // Fill out the modified time structure  
   tmm.tm_hour = 12;  
   tmm.tm_isdst = 0;  
   tmm.tm_mday = 15;  
   tmm.tm_min = 0;  
   tmm.tm_mon = 0;  
   tmm.tm_sec = 0;  
   tmm.tm_year = 102;  
  
   // Convert tm to time_t  
   ut.actime = mktime(&tma);  
   ut.modtime = mktime(&tmm);  
  
   // Show file time before and after  
   system( "dir crt_utime.c" );  
   if( _utime( "crt_utime.c", &ut ) == -1 )  
      perror( "_utime failed\n" );  
   else  
      printf( "File time modified\n" );  
   system( "dir crt_utime.c" );  
}  
```  
  
## Resultados del ejemplo  
  
```  
Volume in drive C has no label.  
 Volume Serial Number is 9CAC-DE74  
  
 Directory of C:\test  
  
01/09/2003  05:38 PM               935 crt_utime.c  
               1 File(s)            935 bytes  
               0 Dir(s)  20,742,955,008 bytes free  
File time modified  
 Volume in drive C has no label.  
 Volume Serial Number is 9CAC-DE74  
  
 Directory of C:\test  
  
01/15/2002  12:00 PM               935 crt_utime.c  
               1 File(s)            935 bytes  
               0 Dir(s)  20,742,955,008 bytes free  
```  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime, \_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_fstat, \_fstat32, \_fstat64, \_fstati64, \_fstat32i64, \_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [\_futime, \_futime32, \_futime64](../../c-runtime-library/reference/futime-futime32-futime64.md)   
 [gmtime, \_gmtime32, \_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime, \_localtime32, \_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [\_stat, \_wstat \(Funciones\)](../../c-runtime-library/reference/stat-functions.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)