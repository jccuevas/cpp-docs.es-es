---
title: ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
ms.date: 4/2/2020
api_name:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
- _o__wctime32
- _o__wctime64
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
ms.openlocfilehash: 6056ad8bac6561c0ce2902928364996b2be9ae92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348245"
---
# <a name="ctime-_ctime32-_ctime64-_wctime-_wctime32-_wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64

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
Puntero al tiempo almacenado para convertir.

## <a name="return-value"></a>Valor devuelto

Puntero al resultado de la cadena de caracteres. **NULL** se devolverá si:

- *sourceTime* representa una fecha antes de la medianoche, 1 de enero de 1970, UTC.

- Si utiliza **_ctime32** o **_wctime32** y *sourceTime* representa una fecha posterior a 23:59:59 18 de enero de 2038, UTC.

- Si utiliza **_ctime64** o **_wctime64** y *sourceTime* representa una fecha posterior a 23:59:59, 31 de diciembre de 3000, UTC.

**ctime** es una función en línea que se evalúa **como _ctime64** y **time_t** es equivalente a **__time64_t**. Si necesita forzar al compilador a interpretar **time_t** como el **antiguo time_t**de 32 bits, puede definir **_USE_32BIT_TIME_T**. Si lo hace, **ctime** se evaluará como **_ctime32**. Esto no es recomendable porque puede producir un error en la aplicación después del 18 de enero de 2038 y no se permite en plataformas de 64 bits.

## <a name="remarks"></a>Observaciones

La función **ctime** convierte un valor de tiempo almacenado como un valor [time_t](../../c-runtime-library/standard-types.md) en una cadena de caracteres. El valor *sourceTime* normalmente se obtiene de una llamada a la [hora,](time-time32-time64.md)que devuelve el número de segundos transcurridos desde la medianoche (00:00:00), 1 de enero de 1970, hora universal coordinada (UTC). La cadena del valor devuelto contiene exactamente 26 caracteres y tiene el formato:

```Output
Wed Jan 02 02:03:55 1980\n\0
```

Se usa un reloj de 24 horas. Todos los campos tienen un ancho constante. El carácter de nueva línea ("\n") y el carácter nulo ("\0") ocupan las dos últimas posiciones de la cadena.

La cadena de caracteres convertidos también se ajusta en función de la configuración de zona horaria local. Consulte las funciones [de hora](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)y [hora local](localtime-localtime32-localtime64.md) para obtener información sobre cómo configurar la hora local y la función [_tzset](tzset.md) para obtener más información sobre cómo definir el entorno de zona horaria y las variables globales.

Una llamada a **ctime** modifica el búfer único asignado estáticamente utilizado por las funciones **gmtime** y **localtime.** Cada llamada a una de estas rutinas destruye el resultado de la llamada anterior. **ctime** comparte un búfer estático con la función **asctime.** Por lo tanto, una llamada a **ctime** destruye los resultados de cualquier llamada anterior a **asctime**, **localtime**o **gmtime**.

**_wctime** y **_wctime64** son la versión de caracteres anchos de **ctime** y **_ctime64;** devolver un puntero a cadena de caracteres anchos. De lo contrario, **_ctime64**, **_wctime**y **_wctime64** comportarse de forma idéntica a **ctime**.

Estas funciones validan sus parámetros. Si *sourceTime* es un puntero nulo, o si el valor *sourceTime* es negativo, estas funciones invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones devuelven **NULL** y **establecen errno en** **EINVAL**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

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

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[Administración de hora](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
