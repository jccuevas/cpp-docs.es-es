---
title: _tzset
ms.date: 4/2/2020
api_name:
- _tzset
- _o__tzset
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tzset
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
ms.openlocfilehash: d5afc1b05f52d73228abc1a1e102c1578eb2d2dc
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912146"
---
# <a name="_tzset"></a>_tzset

Establece variables de tiempo del entorno.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
void _tzset( void );
```

## <a name="remarks"></a>Observaciones

La función **_tzset** usa la configuración actual de la variable de entorno **TZ** para asignar valores a tres variables globales: **_daylight**, **_timezone**y **_tzname**. Estas variables las utilizan las funciones [_ftime](ftime-ftime32-ftime64.md) y [localtime](localtime-localtime32-localtime64.md) para hacer correcciones de la hora universal coordinada (UTC) a la hora local y por la función [Time](time-time32-time64.md) para calcular la hora UTC a partir de la hora del sistema. Use la sintaxis siguiente para establecer la variable de entorno de **TZ** :

> **set TZ =**_TZN_ \[ **+**&#124;**-**]*HH*\[**:**_mm_\[**:**_SS_]] [*DZN*]

|Parámetro|Descripción|
|-|-|
| *tzn* | Nombre de la zona horaria de tres letras, por ejemplo PST. Debe especificar el desplazamiento correcto de la hora local a la hora UTC. |
| *hh* | Diferencia en horas entre las hora UTC y la hora local. Signo (+) opcional para valores positivos. |
| *mm* | Minutos. Separado de *HH* por dos puntos (**:**). |
| *SS* | Segundos. Separado de *mm* por dos puntos (**:**). |
| *dzn* | Zona del horario de verano de tres letras, por ejemplo PDT. Si el horario de verano nunca está en vigor en el emplazamiento, establezca **TZ** sin un valor para *DZN*. La biblioteca en tiempo de ejecución de C usa las reglas de Estados Unidos para implementar el cálculo del horario de verano (DST). |

> [!NOTE]
> Tenga cuidado al calcular el signo de la diferencia de hora. Dado que la diferencia de hora es el desplazamiento de la hora local respecto a la hora UTC (y no a la inversa), el signo puede ser el contrario de lo que cabría esperar intuitivamente. En el caso de las zonas horarias que van por delante de UTC, la diferencia de hora es negativa; en el caso de las que van por detrás de la hora UTC, la diferencia es positiva.

Por ejemplo, para establecer la variable de entorno de **TZ** para que corresponda a la zona horaria actual en Alemania, escriba lo siguiente en la línea de comandos:

> **Set TZ = GST-1GDT**

Este comando utiliza GST para indicar la hora estándar de Alemania, supone que la hora UTC va una hora por detrás de Alemania (es decir, que Alemania va una hora por delante de UTC), y supone que en Alemania se aplica el horario de verano.

Si no se establece el valor de **TZ** , **_tzset** intenta usar la información de zona horaria especificada por el sistema operativo. En el sistema operativo Windows, esta información se especifica en la aplicación de fecha y hora del Panel de control. Si **_tzset** no puede obtener esta información, usa PST8PDT de forma predeterminada, lo que significa la zona horaria del Pacífico.

Según el valor de la variable de entorno **TZ** , se asignan los valores siguientes a las variables globales **_daylight**, **_timezone**y **_tzname** cuando se llama a **_tzset** :

|Variable global|Descripción|Valor predeterminado|
|---------------------|-----------------|-------------------|
|**_daylight**|Valor distinto de cero si se especifica una zona de horario de verano en la configuración de **TZ** ; de lo contrario, es 0.|1|
|**_timezone**|Diferencia en segundos entre las hora local y la hora UTC.|28800 (28800 segundos equivalen a 8 horas)|
|**_tzname**[0]|Valor de cadena del nombre de zona horaria de la variable de entorno **TZ** ; vacío si no se ha establecido **TZ** .|PST|
|**_tzname**[1]|Valor de cadena de la zona horaria de horario de verano; está vacío si la zona de horario de verano se omite de la variable de entorno **TZ** .|PDT|

Los valores predeterminados que se muestran en la tabla anterior para **_daylight** y la matriz de **_tzname** se corresponden con "PST8PDT". Si la zona de DST se omite de la variable de entorno **TZ** , el valor de **_daylight** es 0 y las funciones [_ftime](ftime-ftime32-ftime64.md), [gmtime](gmtime-gmtime32-gmtime64.md)y [localtime](localtime-localtime32-localtime64.md) devuelven 0 para sus marcas de DST.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_tzset**|\<time.h>|

La función **_tzset** es específica de Microsoft. Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
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

## <a name="see-also"></a>Consulte también

[Administración de hora](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
