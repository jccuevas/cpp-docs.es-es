---
title: asctime_s, _wasctime_s
ms.date: 11/04/2016
apiname:
- _wasctime_s
- asctime_s
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
ms.openlocfilehash: fe6ada0d50865897e791fc04b99ec0bb486f5a55
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499989"
---
# <a name="asctime_s-_wasctime_s"></a>asctime_s, _wasctime_s

Convierte una estructura de tiempo de **TM** en una cadena de caracteres. Estas funciones son versiones de [asctime, _wasctime](asctime-wasctime.md) con mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*buffer*<br/>
Un puntero a un búfer para almacenar el resultado de la cadena de caracteres. Esta función presupone un puntero a una ubicación de memoria válida con un tamaño especificado por *numberOfElements*.

*numberOfElements*<br/>
Tamaño del búfer usado para almacenar el resultado.

*tmSource*<br/>
Estructura de fecha y hora. Esta función presupone un puntero a un objeto **struct** **TM** válido.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto. Si hay un error, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, el valor devuelto es un código de error. Los códigos de error se definen en ERRNO.H. Para obtener más información, consulte [errno (Constantes)](../../c-runtime-library/errno-constants.md). Los códigos de error reales devueltos para cada condición de error se muestran en la tabla siguiente.

### <a name="error-conditions"></a>Condiciones de error

|*buffer*|*numberOfElements*|*tmSource*|Volver|Valor en *búfer*|
|--------------|------------------------|----------|------------|-----------------------|
|**NULL**|Cualquiera|Cualquiera|**EINVAL**|No modificado|
|Not **null** (apunta a la memoria válida)|0|Cualquiera|**EINVAL**|No modificado|
|No **null**|0< tamaño < 26|Cualquiera|**EINVAL**|Cadena vacía|
|No **null**|>= 26|**NULL**|**EINVAL**|Cadena vacía|
|No **null**|>= 26|Estructura de hora no válida o valores fuera del intervalo para los componentes del tiempo|**EINVAL**|Cadena vacía|

> [!NOTE]
> Las condiciones de error para **wasctime_s** son similares a **asctime_s** , con la excepción de que el límite de tamaño se mide en palabras.

## <a name="remarks"></a>Comentarios

La función **asctime** convierte una hora almacenada como una estructura en una cadena de caracteres. El valor *tmSource* se suele obtener de una llamada a **gmtime** o **localtime**. Ambas funciones se pueden usar para rellenar una estructura de **TM** , tal y como se define en el tiempo. C.

|miembro de timeptr|Valor|
|--------------------|-----------|
|**tm_hour**|Horas desde la medianoche (0-23)|
|**tm_isdst**|Positivo si el horario de verano está en vigor; 0 si el horario de verano no está en vigor; negativo si se desconoce el estado del horario de verano. La biblioteca en tiempo de ejecución de C usa las reglas de Estados Unidos para implementar el cálculo del horario de verano (DST).|
|**tm_mday**|Día del mes (1-31)|
|**tm_min**|Minutos después de la hora (0-59)|
|**tm_mon**|Mes (0-11; Enero = 0)|
|**tm_sec**|Segundos después del minuto (0-59)|
|**tm_wday**|Día de la semana (0-6; Sunday = 0)|
|**tm_yday**|Día del año (0-365; 1 de enero = 0)|
|**tm_year**|Año (año actual menos 1900)|

La cadena de caracteres convertidos también se ajusta en función de la configuración de zona horaria local. Vea las funciones [time, _time32, _time64](time-time32-time64.md), [_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md) y [localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md) para obtener información sobre cómo configurar la hora local y la función [_tzset](tzset.md) para obtener información sobre cómo definir el entorno de zona horaria y variables globales.

El resultado de la cadena producido por **asctime_s** contiene exactamente 26 caracteres y tiene `Wed Jan 02 02:03:55 1980\n\0`el formato. Se usa un reloj de 24 horas. Todos los campos tienen un ancho constante. El carácter de nueva línea y el carácter nulo ocupan las dos últimas posiciones de la cadena. El valor que se pase como segundo parámetro debe ser al menos igual de grande. Si es menor, se devolverá un código de error, **EINVAL**.

**_wasctime_s** es una versión con caracteres anchos de **asctime_s**. **_wasctime_s** y **asctime_s** se comportan de manera idéntica.

### <a name="generic-text-routine-mapping"></a>Asignación de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**asctime_s**|\<time.h>|
|**_wasctime_s**|\<time.h> o \<wchar.h>|

## <a name="security"></a>Seguridad

Si el puntero de búfer no es **null** y el puntero no señala a un búfer válido, la función sobrescribirá lo que esté en la ubicación. Esto también puede producir una infracción de acceso.

Puede producirse una [saturación del búfer](/windows/win32/SecBP/avoiding-buffer-overruns) si el argumento de tamaño que se pasa es mayor que el tamaño real del búfer.

## <a name="example"></a>Ejemplo

Este programa coloca la hora del sistema en el **aclock**entero largo, lo traduce en la estructura **newtime** y, a continuación, lo convierte en un formato de cadena para la salida, mediante la función **asctime_s** .

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

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
