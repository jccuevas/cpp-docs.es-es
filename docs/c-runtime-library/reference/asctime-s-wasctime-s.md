---
title: asctime_s, _wasctime_s
ms.date: 4/2/2020
api_name:
- _wasctime_s
- asctime_s
- _o__wasctime_s
- _o_asctime_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- asctime_s
- _wasctime_s
- _tasctime_s
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
ms.openlocfilehash: 52391eb1237e4c1d7ef320dacd211b603a21ab8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334225"
---
# <a name="asctime_s-_wasctime_s"></a>asctime_s, _wasctime_s

Convierta una estructura de tiempo **tm** en una cadena de caracteres. Estas funciones son versiones de [asctime, _wasctime](asctime-wasctime.md) con mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t asctime_s(
   char* buffer,
   size_t numberOfElements,
   const struct tm *tmSource
);
errno_t _wasctime_s(
   wchar_t* buffer,
   size_t numberOfElements
   const struct tm *tmSource
);
template <size_t size>
errno_t asctime_s(
   char (&buffer)[size],
   const struct tm *tmSource
); // C++ only
template <size_t size>
errno_t _wasctime_s(
   wchar_t (&buffer)[size],
   const struct tm *tmSource
); // C++ only
```

### <a name="parameters"></a>Parámetros

*Búfer*<br/>
Puntero a un búfer para almacenar el resultado de la cadena de caracteres. Esta función supone un puntero a una ubicación de memoria válida con un tamaño especificado por *numberOfElements*.

*numberOfElements*<br/>
El tamaño del búfer utilizado para almacenar el resultado.

*tmSource*<br/>
Estructura de fecha y hora. Esta función asume un puntero a un objeto **struct** **tm** válido.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto. Si hay un error, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, el valor devuelto es un código de error. Los códigos de error se definen en ERRNO.H. Para obtener más información, consulte [errno (Constantes)](../../c-runtime-library/errno-constants.md). Los códigos de error reales devueltos para cada condición de error se muestran en la tabla siguiente.

### <a name="error-conditions"></a>Condiciones de error

|*Búfer*|*numberOfElements*|*tmSource*|Valor devuelto|Valor en *el búfer*|
|--------------|------------------------|----------|------------|-----------------------|
|**Null**|Any|Any|**EINVAL**|No modificado|
|No **NULL** (señala a la memoria válida)|0|Any|**EINVAL**|No modificado|
|No **NULL**|0< tamaño < 26|Any|**EINVAL**|cadena vacía.|
|No **NULL**|>= 26|**Null**|**EINVAL**|cadena vacía.|
|No **NULL**|>= 26|Estructura de hora no válida o valores fuera del intervalo para los componentes del tiempo|**EINVAL**|cadena vacía.|

> [!NOTE]
> Las condiciones de error para **wasctime_s** son similares a **asctime_s** con la excepción de que el límite de tamaño se mide en palabras.

## <a name="remarks"></a>Observaciones

La función **asctime** convierte un tiempo almacenado como una estructura en una cadena de caracteres. El valor *tmSource* normalmente se obtiene de una llamada a **gmtime** o **localtime**. Ambas funciones se pueden utilizar para rellenar una estructura **tm,** tal como se define en TIEMPO. H.

|miembro de timeptr|Value|
|--------------------|-----------|
|**tm_hour**|Horario desde la medianoche (0-23)|
|**tm_isdst**|Positivo si el horario de verano está en vigor; 0 si el horario de verano no está en vigor; negativo si se desconoce el estado del horario de verano. La biblioteca en tiempo de ejecución de C usa las reglas de Estados Unidos para implementar el cálculo del horario de verano (DST).|
|**tm_mday**|Día del mes (1-31)|
|**tm_min**|Minutos tras hora (0-59)|
|**tm_mon**|Mes (0-11; Enero n.o 0)|
|**tm_sec**|Segundos tras minuto (0-59)|
|**tm_wday**|Día de la semana (0-6; Domingo 0)|
|**tm_yday**|Día del año (0-365; 1 de enero a 0)|
|**tm_year**|Año (año actual menos 1900)|

La cadena de caracteres convertidos también se ajusta en función de la configuración de zona horaria local. Vea las funciones [time, _time32, _time64](time-time32-time64.md), [_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md) y [localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md) para obtener información sobre cómo configurar la hora local y la función [_tzset](tzset.md) para obtener información sobre cómo definir el entorno de zona horaria y variables globales.

El resultado de la cadena generado por **asctime_s** `Wed Jan 02 02:03:55 1980\n\0`contiene exactamente 26 caracteres y tiene el formato . Se usa un reloj de 24 horas. Todos los campos tienen un ancho constante. El carácter de nueva línea y el carácter nulo ocupan las dos últimas posiciones de la cadena. El valor que se pase como segundo parámetro debe ser al menos igual de grande. Si es menor, se devolverá un código de error, **EINVAL**.

**_wasctime_s** es una versión de caracteres anchos de **asctime_s**. **_wasctime_s** y **asctime_s** comportarse de forma idéntica de lo contrario.

Las versiones de la biblioteca de depuración de estas funciones rellenan primero el búfer con 0xFE. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Asignación de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**asctime_s**|\<time.h>|
|**_wasctime_s**|\<time.h> o \<wchar.h>|

## <a name="security"></a>Seguridad

Si el puntero de búfer no es **NULL** y el puntero no apunta a un búfer válido, la función sobrescribirá lo que se encuentra en la ubicación. Esto también puede producir una infracción de acceso.

Puede producirse una [saturación del búfer](/windows/win32/SecBP/avoiding-buffer-overruns) si el argumento de tamaño que se pasa es mayor que el tamaño real del búfer.

## <a name="example"></a>Ejemplo

Este programa coloca la hora del sistema en el entero largo **aclock**, lo traduce en la estructura **newtime** y, a continuación, lo convierte en forma de cadena para la salida, utilizando la función **asctime_s.**

```C
// crt_asctime_s.c
#include <time.h>
#include <stdio.h>

struct tm newtime;
__time32_t aclock;

int main( void )
{
   char buffer[32];
   errno_t errNum;
   _time32( &aclock );   // Get time in seconds.
   _localtime32_s( &newtime, &aclock );   // Convert time to struct tm form.

   // Print local time as a string.

   errNum = asctime_s(buffer, 32, &newtime);
   if (errNum)
   {
       printf("Error code: %d", (int)errNum);
       return 1;
   }
   printf( "Current date and time: %s", buffer );
   return 0;
}
```

```Output
Current date and time: Wed May 14 15:30:17 2003
```

## <a name="see-also"></a>Consulte también

[Administración de hora](../../c-runtime-library/time-management.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
