---
title: ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
ms.date: 11/04/2016
apiname:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
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
- _wctime64
- _ctime32
- _tctime
- _wctime
- _wctime32
- _tctime64
- _ctime64
- ctime
helpviewer_keywords:
- tctime64 function
- _ctime32 function
- ctime32 function
- _wctime function
- wctime64 function
- _tctime64 function
- _tctime32 function
- _ctime64 function
- _wctime64 function
- ctime function
- wctime32 function
- ctime64 function
- _wctime32 function
- _tctime function
- tctime32 function
- tctime function
- wctime function
- time, converting
ms.assetid: 2423de37-a35c-4f0a-a378-3116bc120a9d
ms.openlocfilehash: d1858a36c68a2ca5cedf70a1d74d5f250cbac8df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580831"
---
# <a name="ctime-ctime32-ctime64-wctime-wctime32-wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64

Convierte un valor de hora en cadena y lo ajusta según la configuración de zona horaria local. Hay disponibles versiones más seguras de estas funciones; consulte [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md).

## <a name="syntax"></a>Sintaxis

```C
char *ctime( const time_t *sourceTime );
char *_ctime32( const __time32_t *sourceTime );
char *_ctime64( const __time64_t *sourceTime );
wchar_t *_wctime( const time_t *sourceTime );
wchar_t *_wctime32( const __time32_t *sourceTime );
wchar_t *_wctime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parámetros

*sourceTime*<br/>
Puntero a la hora almacenada para convertir.

## <a name="return-value"></a>Valor devuelto

Puntero al resultado de la cadena de caracteres. **NULL** se devolverá si:

- *sourceTime* representa una fecha anterior a la medianoche del 1 de enero de 1970 UTC.

- Si usas **_ctime32** o **_wctime32** y *sourceTime* representa una fecha posterior a las 23:59:59 del 18 de enero de 2038, UTC.

- Si usas **_ctime64** o **_wctime64** y *sourceTime* representa una fecha posterior a las 23:59:59 del 31 de diciembre de 3000, UTC.

**CTime** es una función insertada que se evalúa como **_ctime64** y **time_t** es equivalente a **__time64_t**. Si necesita forzar el compilador interprete **time_t** como el antiguo 32-bit **time_t**, puede definir **_USE_32BIT_TIME_T**. Al hacerlo, **ctime** se evalúe como **_ctime32**. Esto no es recomendable porque puede producir un error en la aplicación después del 18 de enero de 2038 y no se permite en plataformas de 64 bits.

## <a name="remarks"></a>Comentarios

El **ctime** función convierte un valor de tiempo almacenado como un [time_t](../../c-runtime-library/standard-types.md) valor en una cadena de caracteres. El *sourceTime* valor suele obtenerse de una llamada a [tiempo](time-time32-time64.md), que devuelve el número de segundos transcurrido desde la medianoche (00: 00:00) del 1 de enero de 1970, hora universal coordinada (UTC). La cadena del valor devuelto contiene exactamente 26 caracteres y tiene el formato:

```Output
Wed Jan 02 02:03:55 1980\n\0
```

Se usa un reloj de 24 horas. Todos los campos tienen un ancho constante. El carácter de nueva línea ("\n") y el carácter nulo ("\0") ocupan las dos últimas posiciones de la cadena.

La cadena de caracteres convertidos también se ajusta en función de la configuración de zona horaria local. Consulte la [tiempo](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md), y [localtime](localtime-localtime32-localtime64.md) funciones para obtener información sobre cómo configurar la hora local y la [_tzset](tzset.md) funcionar para detalles sobre cómo definir el entorno de zona horaria y variables globales.

Una llamada a **ctime** modifica el búfer asignado estáticamente único utilizado por el **gmtime** y **localtime** funciones. Cada llamada a una de estas rutinas destruye el resultado de la llamada anterior. **CTime** comparte un búfer estático con el **asctime** función. Por lo tanto, una llamada a **ctime** destruye los resultados de las llamadas anteriores a **asctime**, **localtime**, o **gmtime**.

**_wctime** y **_wctime64** son la versión de caracteres anchos de **ctime** y **_ctime64**; devuelve un puntero a la cadena de caracteres anchos. En caso contrario, **_ctime64**, **_wctime**, y **_wctime64** se comportan de forma idéntica a **ctime**.

Estas funciones validan sus parámetros. Si *sourceTime* es un puntero nulo, o si el *sourceTime* valor es negativo, estas funciones invocan el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones devuelven **NULL** y establecer **errno** a **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime**|**ctime**|**ctime**|**_wctime**|
|**_tctime32**|**_ctime32**|**_ctime32**|**_wctime32**|
|**_tctime64**|**_ctime64**|**_ctime64**|**_wctime64**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**ctime**|\<time.h>|
|**_ctime32**|\<time.h>|
|**_ctime64**|\<time.h>|
|**_wctime**|\<time.h> o \<wchar.h>|
|**_wctime32**|\<time.h> o \<wchar.h>|
|**_wctime64**|\<time.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_ctime64.c
// compile with: /W3
/* This program gets the current
* time in _time64_t form, then uses ctime to
* display the time in string form.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   __time64_t ltime;

   _time64( &ltime );
   printf( "The time is %s\n", _ctime64( &ltime ) ); // C4996
   // Note: _ctime64 is deprecated; consider using _ctime64_s
}
```

```Output
The time is Wed Feb 13 16:04:43 2002
```

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
