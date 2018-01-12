---
title: _tzset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _tzset
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
f1_keywords: _tzset
dev_langs: C++
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f103da7ca67721f6c654c593746b9427954c6930
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tzset"></a>_tzset
Establece variables de tiempo del entorno.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea                  [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _tzset( void );  
```  
  
## <a name="remarks"></a>Comentarios  
 La función `_tzset` usa la configuración actual de la variable de entorno `TZ` para asignar valores a tres variables globales: `_daylight`, `_timezone`y `_tzname`. Las funciones [_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) y [localtime](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) usan estas variables para ajustar la hora universal coordinada (UTC) a la hora local. La función `time` las usa para calcular la hora UTC a partir de la hora del sistema. Use la sintaxis siguiente para establecer la variable de entorno `TZ` :  
  
 `set` `TZ`=`tzn`[+ &#124; -]`hh`[`:mm`[`:ss`] ][`dzn`]  
  
 `tzn`  
 Nombre de la zona horaria de tres letras, por ejemplo PST. Debe especificar el desplazamiento correcto de la hora local a la hora UTC.  
  
 `hh`  
 Diferencia en horas entre las hora UTC y la hora local. Signo (+) opcional para valores positivos.  
  
 `mm`  
 Minutos. Se separa de `hh` mediante dos puntos (`:`).  
  
 `ss`  
 Segundos. Se separa de `mm` mediante dos puntos (`:`).  
  
 `dzn`  
 Zona del horario de verano de tres letras, por ejemplo PDT. Si el horario de verano no se aplica nunca en el lugar, establezca `TZ` sin valor para `dzn`. La biblioteca en tiempo de ejecución de C usa las reglas de Estados Unidos para implementar el cálculo del horario de verano (DST).  
  
> [!NOTE]
>  Tenga cuidado al calcular el signo de la diferencia de hora. Dado que la diferencia de hora es el desplazamiento de la hora local respecto a la hora UTC (y no a la inversa), el signo puede ser el contrario de lo que cabría esperar intuitivamente. En el caso de las zonas horarias que van por delante de UTC, la diferencia de hora es negativa; en el caso de las que van por detrás de la hora UTC, la diferencia es positiva.  
  
 Por ejemplo, para establecer la variable de entorno `TZ` correspondiente a la zona horaria actual en Alemania, escriba lo siguiente en la línea de comandos:  
  
```  
set TZ=GST-1GDT  
```  
  
 Este comando utiliza GST para indicar la hora estándar de Alemania, supone que la hora UTC va una hora por detrás de Alemania (es decir, que Alemania va una hora por delante de UTC), y supone que en Alemania se aplica el horario de verano.  
  
 Si el `TZ` valor no está establecido, `_tzset` intenta utilizar la información de zona horaria especificada por el sistema operativo. En el sistema operativo Windows, esta información se especifica en la aplicación de fecha y hora del Panel de control. Si `_tzset` no puede obtener esta información, usa PST8PDT de forma predeterminada, que indica la zona horaria del Pacífico.  
  
 En función del valor de la variable de entorno `TZ` , se asignan los valores siguientes a las variables globales `_daylight`, `_timezone`y `_tzname` cuando se llama a `_tzset` :  
  
|Variable global|Descripción|Valor predeterminado|  
|---------------------|-----------------|-------------------|  
|`_daylight`|Valor distinto de cero si se especifica una zona de horario de verano en la configuración de `TZ` ; de lo contrario, 0.|1|  
|`_timezone`|Diferencia en segundos entre las hora local y la hora UTC.|28800 (28800 segundos equivalen a 8 horas)|  
|`_tzname`[0]|Valor de cadena del nombre de la zona horaria de la variable de entorno `TZ` ; está vacío si `TZ` no se ha establecido.|PST|  
|`_tzname`[1]|Valor de cadena de la zona de horario de verano; está vacío si la zona de horario de verano se omite de la variable de entorno `TZ`.|PDT|  
  
 Los valores predeterminados de la tabla anterior para `_daylight` y la matriz de `_tzname` corresponden a “PST8PDT”. Si la zona de DST se omite en la variable de entorno `TZ` , el valor de `_daylight` es 0 y las funciones `_ftime`, `gmtime`y `localtime` devuelven 0 para sus marcas de DST.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_tzset`|\<time.h>|  
  
 Para más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_tzset.cpp  
// This program uses _tzset to set the global variables  
// named _daylight, _timezone, and _tzname. Since TZ is  
// not being explicitly set, it uses the system time.  
  
#include <time.h>  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
    _tzset();  
    int daylight;  
    _get_daylight( &daylight );  
    printf( "_daylight = %d\n", daylight );  
    long timezone;  
    _get_timezone( &timezone );  
    printf( "_timezone = %ld\n", timezone );  
    size_t s;  
    char tzname[100];  
    _get_tzname( &s, tzname, sizeof(tzname), 0 );  
    printf( "_tzname[0] = %s\n", tzname );  
    exit( 0 );  
}  
```  
  
```Output  
_daylight = 1  
_timezone = 28800  
_tzname[0] = Pacific Standard Time  
```  
  
## <a name="see-also"></a>Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)