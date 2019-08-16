---
title: _tzset
ms.date: 11/04/2016
apiname:
- _tzset
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
- _tzset
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
ms.openlocfilehash: 6312297e6daa9b4790674bd26d21812d5bee34c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385198"
---
# <a name="tzset"></a>_tzset

Establece variables de tiempo del entorno.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
void _tzset( void );
```

## <a name="remarks"></a>Comentarios

El **_tzset** función usa la configuración actual de la variable de entorno **TZ** para asignar valores a tres variables globales: **_daylight**, **_timezone** , y **_tzname**. Estas variables se usan por el [_ftime](ftime-ftime32-ftime64.md) y [localtime](localtime-localtime32-localtime64.md) funciones para realizar correcciones de hora universal coordinada (UTC) a la hora local y por la [tiempo](time-time32-time64.md) función calcular la hora UTC de la hora del sistema. Use la siguiente sintaxis para establecer el **TZ** variable de entorno:

> **set TZ=**_tzn_ \[**+**&#124;**-**]*hh*\[**:**_mm_\[**:**_ss_] ][*dzn*]

|Parámetro|Descripción|
|-|-|
| *tzn* | Nombre de la zona horaria de tres letras, por ejemplo PST. Debe especificar el desplazamiento correcto de la hora local a la hora UTC. |
| *hh* | Diferencia en horas entre las hora UTC y la hora local. Signo (+) opcional para valores positivos. |
| *mm* | Minutos. Separada de *hh* por dos puntos (**:**). |
| *ss* | Segundos. Separada de *mm* por dos puntos (**:**). |
| *dzn* | Zona del horario de verano de tres letras, por ejemplo PDT. Si el horario de verano nunca está en vigor en el grado de emplazamiento, establezca **TZ** sin un valor para *dzn*. La biblioteca en tiempo de ejecución de C usa las reglas de Estados Unidos para implementar el cálculo del horario de verano (DST). |

> [!NOTE]
> Tenga cuidado al calcular el signo de la diferencia de hora. Dado que la diferencia de hora es el desplazamiento de la hora local respecto a la hora UTC (y no a la inversa), el signo puede ser el contrario de lo que cabría esperar intuitivamente. En el caso de las zonas horarias que van por delante de UTC, la diferencia de hora es negativa; en el caso de las que van por detrás de la hora UTC, la diferencia es positiva.

Por ejemplo, para establecer el **TZ** variable de entorno para que coincida con la zona horaria actual en Alemania, escriba lo siguiente en la línea de comandos:

> **establecer TZ = GST 1GDT**

Este comando utiliza GST para indicar la hora estándar de Alemania, supone que la hora UTC va una hora por detrás de Alemania (es decir, que Alemania va una hora por delante de UTC), y supone que en Alemania se aplica el horario de verano.

Si el **TZ** no se establece el valor, **_tzset** intenta utilizar la información de zona horaria especificada por el sistema operativo. En el sistema operativo Windows, esta información se especifica en la aplicación de fecha y hora del Panel de control. Si **_tzset** no se puede obtener esta información, usa PST8PDT de forma predeterminada, lo que significa la zona horaria del Pacífico.

Según el **TZ** valor de variable de entorno, los siguientes valores se asignan a las variables globales **_daylight**, **_timezone**, y **_tzname** cuando **_tzset** se denomina:

|Variable global|Descripción|Valor predeterminado|
|---------------------|-----------------|-------------------|
|**_daylight**|Un valor distinto de cero si se especifica una zona de horario de verano en **TZ** establecer; en caso contrario, 0.|1|
|**_timezone**|Diferencia en segundos entre las hora local y la hora UTC.|28800 (28800 segundos equivalen a 8 horas)|
|**_tzname**[0]|Valor de cadena del nombre de zona horaria de **TZ** variable de entorno; está vacío si **TZ** no se ha establecido.|PST|
|**_tzname**[1]|Valor de cadena de zona de horario de verano; vacío si se omite la zona de horario de verano de **TZ** variable de entorno.|PDT|

Los valores predeterminados que se muestra en la tabla anterior para **_daylight** y **_tzname** matriz corresponden a "PST8PDT". Si la zona de DST se omite en la **TZ** variable de entorno, el valor de **_daylight** es 0 y el [_ftime](ftime-ftime32-ftime64.md), [gmtime](gmtime-gmtime32-gmtime64.md)y [localtime](localtime-localtime32-localtime64.md) funciones devuelven 0 para sus marcas de DST.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_tzset**|\<time.h>|

El **_tzset** función es específico de Microsoft. Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
