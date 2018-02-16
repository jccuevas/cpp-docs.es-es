---
title: mktime, _mktime32, _mktime64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _mktime32
- mktime
- _mktime64
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
- mktime
- _mktime64
dev_langs:
- C++
helpviewer_keywords:
- _mktime32 function
- mktime function
- time functions
- mktime64 function
- converting times
- mktime32 function
- _mktime64 function
- time, converting
ms.assetid: 284ed5d4-7064-48a2-bd50-15effdae32cf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee2673f98f219559fd42d192dd934c8fe3eaed8c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="mktime-mktime32-mktime64"></a>mktime, _mktime32, _mktime64
Convierte la hora local en un valor de calendario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
time_t mktime(  
   struct tm *timeptr   
);  
__time32_t _mktime32(  
   struct tm *timeptr   
);  
__time64_t _mktime64(  
   struct tm *timeptr   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *timeptr*  
 Puntero a la estructura de hora; vea [asctime](../../c-runtime-library/reference/asctime-wasctime.md).  
  
## <a name="return-value"></a>Valor devuelto  
 `_mktime32` devuelve la hora de calendario especificada codificada como valor de tipo [time_t](../../c-runtime-library/standard-types.md). Si *timeptr* hace referencia a una fecha anterior a la medianoche del 1 de enero de 1970, o si no se puede representar la hora de calendario, `_mktime32` devuelve -1 que se convierte al tipo `time_t`. Cuando se usa `_mktime32` y si *timeptr* hace referencia a una fecha posterior a las 23:59:59 del 18 de enero de 2038, hora Universal coordinada (UTC), devolverá -1 que se convierte al tipo `time_t`.  
  
 `_mktime64` se devolverá -1 que se convierte al tipo `__time64_t` si *timeptr* hace referencia a una fecha posterior a 23:59:59 del 31 de diciembre de 3000, UTC.  
  
## <a name="remarks"></a>Comentarios  
 Las funciones `mktime`, `_mktime32` y `_mktime64` convierten la estructura de tiempo proporcionada (posiblemente incompleta) a la que señala *timeptr* en una estructura totalmente definida con valores normalizados y, después, la convierte en un valor de tiempo de calendario de `time_t`. El tiempo convertido tiene la misma codificación que los valores devueltos por la función [time](../../c-runtime-library/reference/time-time32-time64.md). Se omiten los valores originales de los componentes `tm_wday` y `tm_yday` de la estructura *timeptr* y los valores originales de los demás componentes no se limitan a los intervalos normales.  
  
 `mktime` es una función insertada equivalente a `_mktime64`, a menos que `_USE_32BIT_TIME_T` esté definido, en cuyo caso equivale a `_mktime32`.  
  
 Después de un ajuste a la hora UTC, `_mktime32` controla las fechas desde la medianoche del 1 de enero de 1970 hasta las 23:59:59 del 18 de enero de 2038, hora UTC. `_mktime64` controla las fechas desde la medianoche del 1 de enero de 1970 a las 23:59:59 del 31 de diciembre de 3000. Este ajuste puede hacer que estas funciones devuelvan -1 (convertido en `time_t`, `__time32_t` o `__time64_t`), aunque la fecha especificada esté dentro del intervalo. Por ejemplo, si se encuentra en El Cairo (Egipto), que va dos horas por delante de UTC, primero se restarán dos horas de la fecha que especifique en *timeptr*, lo que puede poner la fecha fuera del intervalo.  
  
 Estas funciones se pueden usar para validar y rellenar una estructura de tm. Si se ejecutan correctamente, estas funciones establecen los valores de `tm_wday` y `tm_yday` como corresponda, y establecen los demás componentes de forma que representen la hora de calendario especificada, pero con los valores dentro de los intervalos normales. El valor final de `tm_mday` no se establece hasta que se determinen `tm_mon` y `tm_year`. Al especificar una estructura de hora de `tm`, establezca el campo `tm_isdst` en:  
  
-   Cero (0) para indicar que está vigente la hora estándar.  
  
-   Un valor mayor que 0 para indicar que está vigente el horario de verano.  
  
-   Un valor menor que cero para que el código de la biblioteca en tiempo de ejecución de C calcule si está vigente la hora estándar o el horario de verano.  
  
 La biblioteca en tiempo de ejecución de C determinará el comportamiento del horario de verano partiendo de la variable de entorno [TZ](../../c-runtime-library/reference/tzset.md). Si `TZ` no está establecido, se usa la llamada a [GetTimeZoneInformation](http://msdn.microsoft.com/library/windows/desktop/ms724421.aspx) de la API de Win32 para obtener la información del horario de verano del sistema operativo. Si se produce un error, la biblioteca supone que se usan las reglas de Estados Unidos para implementar el cálculo del horario de verano. `tm_isdst` es un campo obligatorio. Si no se establece, su valor es indefinido y el valor devuelto de estas funciones es imprevisible. Si *timeptr* señala a una estructura `tm` devuelta por una llamada anterior a `asctime`, `gmtime` o `localtime` (o a las variantes de estas funciones), el campo `tm_isdst` contiene el valor correcto.  
  
 Observe que `gmtime` y `localtime` (y `_gmtime32`, `_gmtime64`, `_localtime32` y `_localtime64`) usan un único búfer por subproceso para la conversión. Si proporciona este búfer a `mktime`, `_mktime32` o `_mktime64`, se destruye el contenido anterior.  
  
 Estas funciones validan su parámetro. Si *timeptr* es un puntero nulo, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones devuelven -1 y establecen `errno` en `EINVAL`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`mktime`|\<time.h>|  
|`_mktime32`|\<time.h>|  
|`_mktime64`|\<time.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_mktime.c  
/* The example takes a number of days  
 * as input and returns the time, the current  
 * date, and the specified number of days.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   struct tm  when;  
   __time64_t now, result;  
   int        days;  
   char       buff[80];  
  
   time( &now );  
   _localtime64_s( &when, &now );  
   asctime_s( buff, sizeof(buff), &when );  
   printf( "Current time is %s\n", buff );  
   days = 20;  
   when.tm_mday = when.tm_mday + days;  
   if( (result = mktime( &when )) != (time_t)-1 ) {  
      asctime_s( buff, sizeof(buff), &when );  
      printf( "In %d days the time will be %s\n", days, buff );  
   } else  
      perror( "mktime failed" );  
}  
```  
  
## <a name="sample-output"></a>Resultados del ejemplo  
  
```  
Current time is Fri Apr 25 13:34:07 2003  
  
In 20 days the time will be Thu May 15 13:34:07 2003  
```  
  
## <a name="see-also"></a>Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [_mkgmtime, _mkgmtime32, _mkgmtime64](../../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)