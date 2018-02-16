---
title: _utime, _utime32, _utime64, _wutime, _wutime32, _wutime64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tutime
- _utime64
- wutime
- utime32
- wutime64
- _utime
- wutime32
- _wutime
- utime
- utime64
- _wutime64
- _utime32
- _tutime64
- _wutime32
dev_langs:
- C++
helpviewer_keywords:
- tutime function
- utime32 function
- utime64 function
- _utime function
- _tutime32 function
- time [C++], file modification
- wutime function
- _wutime function
- _wutime32 function
- _tutime64 function
- _tutime function
- files [C++], modification time
- _wutime64 function
- _utime32 function
- utime function
- _utime64 function
- wutime64 function
- wutime32 function
- tutime64 function
- tutime32 function
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f94c67fe75f5675192dbd0f306d8eef0aace70f5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="utime-utime32-utime64-wutime-wutime32-wutime64"></a>_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64
Establece la hora de modificación de un archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `filename`  
 Puntero a una cadena que contiene la ruta de acceso o el nombre de archivo.  
  
 `times`  
 Puntero a los valores de hora almacenados.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se ha cambiado la hora de modificación de archivo, cada una de estas funciones devuelve 0. Un valor devuelto de -1 indica un error. Si se pasa un parámetro no válido, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y `errno` se establece en uno de los siguientes valores:  
  
 `EACCES`  
 La ruta de acceso especifica un directorio o un archivo de solo lectura  
  
 `EINVAL`  
 Argumento `times` no válido  
  
 `EMFILE`  
 Demasiados archivos abiertos (se debe abrir el archivo para cambiar su hora de modificación)  
  
 `ENOENT`  
 Ruta de acceso o nombre de archivo no encontrado  
  
 Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.  
  
 La fecha de un archivo se puede cambiar si la fecha de modificación es posterior a la medianoche del 1 de enero de 1970 y anterior a la fecha de finalización de la función empleada. `_utime` y `_wutime` usan un valor de hora de 64 bits, por lo que la fecha de finalización es 23:59:59, 31 de diciembre de 3000, UTC. Si `_USE_32BIT_TIME_T` se define para forzar el comportamiento anterior, la fecha de finalización es 23:59:59, 18 de enero de 2038, UTC. `_utime32` o `_wutime32` usan un tipo de hora de 32 bits independientemente de si `_USE_32BIT_TIME_T` está definido y siempre tienen la fecha de finalización más temprana. `_utime64` o `_wutime64` usan siempre el tipo de hora de 64 bits, por lo que en todo momento admiten la fecha de finalización más tardía.  
  
## <a name="remarks"></a>Comentarios  
 La función `_utime` establece la hora de modificación del archivo especificado por `filename`*.* El proceso debe tener acceso de escritura al archivo para cambiar la hora. En el sistema operativo Windows, puede cambiar la hora de acceso y de modificación en la estructura `_utimbuf`. Si `times` es un puntero `NULL`, la hora de modificación se establece en la hora local actual. De lo contrario, `times` debe apuntar a una estructura de tipo `_utimbuf`, definida en SYS\UTIME.H.  
  
 La estructura `_utimbuf` almacena las horas de acceso a archivos y de modificación usadas por `_utime` para cambiar las fechas de modificación de archivos. La estructura tiene los dos campos siguientes, que son de tipo `time_t`:  
  
 `actime`  
 Hora de acceso a archivos  
  
 `modtime`  
 Hora de modificación de archivos  
  
 Las versiones específicas de la estructura `_utimbuf` (`_utimebuf32` y `__utimbuf64`) se definen mediante las versiones de 32 y 64 bits del tipo de hora. Se usan en las versiones específicas de 32 y 64 bits de esta función. `_utimbuf` de forma predeterminada usa un tipo de hora de 64 bits, a menos que `_USE_32BIT_TIME_T` esté definido.  
  
 `_utime` es idéntico a `_futime`, excepto que el argumento `filename` de `_utime` es un nombre de archivo o una ruta de acceso a un archivo en lugar de un descriptor de archivo de un archivo abierto.  
  
 `_wutime` es una versión con caracteres anchos de `_utime`; el argumento `filename` para `_wutime` es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tutime`|`_utime`|`_utime`|`_wutime`|  
|`_tutime32`|`_utime32`|`_utime32`|`_wutime32`|  
|`_tutime64`|`_utime64`|`_utime64`|`_wutime64`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezados obligatorios|Encabezados opcionales|  
|-------------|----------------------|----------------------|  
|`_utime`, `_utime32`, `_utime64`|\<sys/utime.h>|\<errno.h>|  
|`_utime64`|\<sys/utime.h>|\<errno.h>|  
|`_wutime`|\<utime.h> o \<wchar.h>|\<errno.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Este programa usa `_utime` para establecer la hora de modificación del archivo en la hora actual.  
  
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
  
## <a name="sample-output"></a>Resultados del ejemplo  
  
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
  
## <a name="see-also"></a>Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [_futime, _futime32, _futime64](../../c-runtime-library/reference/futime-futime32-futime64.md)   
 [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [_stat, _wstat (Funciones)](../../c-runtime-library/reference/stat-functions.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)