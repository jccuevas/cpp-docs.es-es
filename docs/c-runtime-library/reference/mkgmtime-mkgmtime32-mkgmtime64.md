---
title: _mkgmtime, _mkgmtime32, _mkgmtime64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
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
- _mkgmtime64
- mkgmtime32
- _mkgmtime32
- mkgmtime
- mkgmtime64
- _mkgmtime
dev_langs:
- C++
helpviewer_keywords:
- mkgmtime32 function
- time functions
- mkgmtime function
- _mkgmtime function
- converting times
- mkgmtime64 function
- _mkgmtime64 function
- _mkgmtime32 function
- time, converting
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 7f73bffc2971b535f393cef7e0e2f957b01eee42
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="mkgmtime-mkgmtime32-mkgmtime64"></a>_mkgmtime, _mkgmtime32, _mkgmtime64
Convierte una hora UTC representada por un `tm``struct` en una hora UTC representada por un tipo `time_t`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      time_t _mkgmtime(  
   struct tm* timeptr  
);  
__time32_t _mkgmtime32(  
   struct tm* timeptr  
);  
__time64_t _mkgmtime64(  
   struct tm* timeptr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `timeptr`  
 Puntero a la hora UTC como `struct``tm` que se debe convertir.  
  
## <a name="return-value"></a>Valor devuelto  
 Cantidad de tipo `__time32_t` o `__time64_t` que representa el número de segundos transcurridos desde la medianoche del 1 de enero de 1970, hora universal coordinada (UTC). Si la fecha está fuera del intervalo (vea la sección Comentarios) o la entrada no se puede interpretar como una hora válida, el valor devuelto es -1.  
  
## <a name="remarks"></a>Comentarios  
 Las funciones `_mkgmtime32` y `_mkgmtime64` convierten una hora UTC en un tipo `__time32_t` o `__time64_t` que representa la hora con el formato UTC. Para convertir una hora local en hora UTC, use `mktime`, `_mktime32` y `_mktime64`.  
  
 `_mkgmtime` es una función insertada que se evalúa como `_mkgmtime64` y `time_t` es equivalente a `__time64_t`. Si necesita forzar el compilador para interpretar `time_t` como el antiguo `time_t`de 32 bits, puede definir `_USE_32BIT_TIME_T`. Esto, sin embargo, no es recomendable porque puede producir un error en la aplicación después del 18 de enero de 2038 (el intervalo máximo de un `time_t` de 32 bits), y no se permite en absoluto en ninguna de las plataformas de 64 bits.  
  
 La estructura de tiempo que se haya pasado cambiará del siguiente modo, de la misma manera en que cambian con las funciones `_mktime`: los campos `tm_wday` y `tm_yday` se establecen en valores nuevos basados en los valores de `tm_mday` y `tm_year`. Al especificar una estructura de hora de `tm`, establezca el campo `tm_isdst` en:  
  
-   Cero (0) para indicar que está vigente la hora estándar.  
  
-   Un valor mayor que 0 para indicar que está vigente el horario de verano.  
  
-   Un valor menor que cero para que el código de la biblioteca en tiempo de ejecución de C calcule si está vigente la hora estándar o el horario de verano.  
  
 La biblioteca en tiempo de ejecución de C usa la variable de entorno TZ para determinar el horario de verano correcto. Si TZ no está establecido, se consulta al sistema operativo para obtener el comportamiento correcto del horario de verano regional. `tm_isdst` es un campo obligatorio. Si no se establece, su valor es indefinido y el valor devuelto de `mktime` es imprevisible.  
  
 El intervalo de la función `_mkgmtime32` va desde la medianoche del 1 de enero de 1970 (hora UTC) hasta las 23:59:59 del 18 de enero de 2038 (hora UTC). El intervalo de `_mkgmtime64` va desde la medianoche del 1 de enero de 1970 (hora UTC) hasta las 23:59:59 del 31 de diciembre de 3000 (hora UTC). Una fecha fuera de intervalo da como resultado un valor devuelto de -1. El intervalo de `_mkgmtime` depende de si `_USE_32BIT_TIME_T` está definido. Si no se define (comportamiento predeterminado), el intervalo será el de `_mkgmtime64`; en caso contrario, el intervalo se limitará al rango de 32 bits de `_mkgmtime32`.  
  
 Tenga en cuenta que `gmtime` y `localtime` usan un solo búfer asignado estáticamente para la conversión. Si proporciona este búfer a `mkgmtime`, se destruye el contenido anterior.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_mkgmtime.c  
#include <stdio.h>  
#include <time.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t now, mytime, gmtime;  
    char buff[30];  
  
    time( & now );  
  
    _localtime64_s( &t1, &now );  
    _gmtime64_s( &t2, &now );  
  
    mytime = mktime(&t1);  
    gmtime = _mkgmtime(&t2);  
  
    printf("Seconds since midnight, January 1, 1970\n");  
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);  
  
    /* Use asctime_s to display these times. */  
  
    _localtime64_s( &t1, &mytime );  
    asctime_s( buff, sizeof(buff), &t1 );  
    printf( "Local Time: %s\n", buff );  
  
    _gmtime64_s( &t2, &gmtime );  
    asctime_s( buff, sizeof(buff), &t2 );  
    printf( "Greenwich Mean Time: %s\n", buff );  
  
}  
```  
  
## <a name="sample-output"></a>Resultados del ejemplo  
  
```  
Seconds since midnight, January 1, 1970  
My time: 1171588492  
GM time (UTC): 1171588492  
  
Local Time: Thu Feb 15 17:14:52 2007  
  
Greenwich Mean Time: Fri Feb 16 01:14:52 2007  
```  
  
 En el ejemplo siguiente se muestra cómo se rellena la estructura incompleta con los valores calculados del día de la semana y el día del año.  
  
```  
// crt_mkgmtime2.c  
#include <stdio.h>  
#include <time.h>  
#include <memory.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t gmtime;  
    char buff[30];  
  
    memset(&t1, 0, sizeof(struct tm));  
    memset(&t2, 0, sizeof(struct tm));  
  
    t1.tm_mon = 1;  
    t1.tm_isdst = 0;  
    t1.tm_year = 103;  
    t1.tm_mday = 12;  
  
    // The day of the week and year will be incorrect in the output here.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
    gmtime = _mkgmtime(&t1);  
  
    // The correct day of the week and year were determined.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
}  
```  
  
## <a name="output"></a>Salida  
  
```  
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003  
 t.tm_yday = 0  
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003  
 t.tm_yday = 42  
```  
  
## <a name="see-also"></a>Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime, _mktime32, _mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)
