---
title: asctime, _wasctime | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wasctime
- asctime
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
- _tasctime
- asctime
- _wasctime
dev_langs:
- C++
helpviewer_keywords:
- asctime function
- tasctime function
- wasctime function
- _tasctime function
- _wasctime function
- time structure conversion
- time, converting
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 91f0ffd5b02f9e8bc34604683c6274ec0f2c28b3
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="asctime-wasctime"></a>asctime, _wasctime
Convierta una estructura de hora `tm` en una cadena de caracteres. Hay disponibles versiones más seguras de estas funciones; consulte [asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
char *asctime(   
   const struct tm *timeptr   
);  
wchar_t *_wasctime(   
   const struct tm *timeptr   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `timeptr`  
 Estructura de fecha y hora.  
  
## <a name="return-value"></a>Valor devuelto  
 `asctime` devuelve un puntero al resultado de la cadena de caracteres; `_wasctime` devuelve un puntero al resultado de la cadena de caracteres anchos. No hay ningún error de valor devuelto.  
  
## <a name="remarks"></a>Comentarios  
 Hay disponibles versiones más seguras de estas funciones; consulte [asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md).  
  
 La función `asctime` convierte una hora almacenada como estructura en una cadena de caracteres. El valor `timeptr` suele obtenerse de una llamada a `gmtime` o `localtime`, que devuelven un puntero a una estructura `tm`, que se define en TIME.H.  
  
|miembro de timeptr|Valor|  
|--------------------|-----------|  
|`tm_hour`|Horas desde la medianoche (0-23)|  
|`tm_isdst`|Positivo si el horario de verano está en vigor; 0 si el horario de verano no está en vigor; negativo si se desconoce el estado del horario de verano. La biblioteca en tiempo de ejecución de C usa las reglas de Estados Unidos para implementar el cálculo del horario de verano (DST).|  
|`tm_mday`|Día del mes (1-31)|  
|`tm_min`|Minutos después de la hora (0-59)|  
|`tm_mon`|Mes (0-11; Enero = 0)|  
|`tm_sec`|Segundos después del minuto (0-59)|  
|`tm_wday`|Día de la semana (0-6; El domingo = 0)|  
|`tm_yday`|Día del año (0-365; El 1 de enero = 0)|  
|`tm_year`|Año (año actual menos 1900)|  
  
 La cadena de caracteres convertidos también se ajusta en función de la configuración de zona horaria local. Para obtener información sobre cómo configurar la hora local, vea las funciones [time](../../c-runtime-library/reference/time-time32-time64.md), [_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) y [localtime](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) y la función [_tzset](../../c-runtime-library/reference/tzset.md) para obtener información sobre cómo definir el entorno de zona horaria y variables globales.  
  
 El resultado de cadena que `asctime` genera contiene exactamente 26 caracteres y tiene el formato `Wed Jan 02 02:03:55 1980\n\0`. Se usa un reloj de 24 horas. Todos los campos tienen un ancho constante. El carácter de nueva línea y el carácter nulo ocupan las dos últimas posiciones de la cadena. `asctime` usa un único búfer asignado estáticamente que contiene la cadena de devolución. Cada llamada a esta función destruye el resultado de la llamada anterior.  
  
 `_wasctime` es una versión con caracteres anchos de `asctime`. Por lo demás, `_wasctime` y `asctime` se comportan de forma idéntica.  
  
 Estas funciones validan sus parámetros. Si `timeptr` es un puntero nulo o contiene valores fuera del intervalo, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve `NULL` y establece en `errno` en `EINVAL`.  
  
### <a name="generic-text-routine-mapping"></a>Asignación de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tasctime`|`asctime`|`asctime`|`_wasctime`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`asctime`|\<time.h>|  
|`_wasctime`|\<time.h> o \<wchar.h>|  
  
## <a name="example"></a>Ejemplo  
 Este programa inserta la hora del sistema en la `aclock` de entero largo, la convierte en la estructura `newtime` y luego la convierte a formato de cadena de salida, con la función `asctime`.  
  
```  
// crt_asctime.c  
// compile with: /W3  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
    struct tm   *newTime;  
    time_t      szClock;  
  
    // Get time in seconds  
    time( &szClock );  
  
    // Convert time to struct tm form   
    newTime = localtime( &szClock );  
  
    // Print local time as a string.  
    printf_s( "Current date and time: %s", asctime( newTime ) ); // C4996  
    // Note: asctime is deprecated; consider using asctime_s instead  
}  
```  
  
```Output  
Current date and time: Sun Feb 03 11:38:58 2002  
```  
  
## <a name="see-also"></a>Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)   
 [asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)
