---
title: ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s
ms.date: 4/2/2020
api_name:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
- _o__ctime32_s
- _o__ctime64_s
- _o__wctime32_s
- _o__wctime64_s
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
- ctime64_s
- _ctime32_s
- _tctime32_s
- _ctime64_s
- _wctime_s
- _tctime_s
- _tctime64_s
- ctime_s
- ctime32_s
helpviewer_keywords:
- _wctime32_s function
- ctime64_s function
- _tctime64_s function
- _wctime_s function
- tctime_s function
- _wctime64_s function
- ctime_s function
- ctime32_s function
- _ctime64_s function
- tctime64_s function
- wctime64_s function
- wctime_s function
- _tctime_s function
- tctime32_s function
- wctime32_s function
- time, converting
- _ctime32_s function
- _tctime32_s function
ms.assetid: 36ac419a-8000-4389-9fd8-d78b747a009b
ms.openlocfilehash: ca7636f7054b6c7e228b57e0e776250f1b4ccb32
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914817"
---
# <a name="ctime_s-_ctime32_s-_ctime64_s-_wctime_s-_wctime32_s-_wctime64_s"></a>ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s

Convierte un valor de hora en cadena y lo ajusta según la configuración de zona horaria local. Se trata de versiones de [ctime, _ctime64, _wctime, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) con mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t ctime_s(
   char* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _ctime32_s(
   char* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _ctime64_s(
   char* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime )
;
errno_t _wctime_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _wctime32_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _wctime64_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime
);
```

```cpp
template <size_t size>
errno_t _ctime32_s(
   char (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _ctime64_s(
   char (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime32_s(
   wchar_t (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime64_s(
   wchar_t (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
```

### <a name="parameters"></a>Parámetros

*búfer*<br/>
Debe ser lo suficientemente grande como para contener 26 caracteres. Un puntero al resultado de la cadena de caracteres o **null** si:

- *sourceTime* representa una fecha anterior a la medianoche del 1 de enero de 1970, hora UTC.

- Si usa **_ctime32_s** o **_wctime32_s** y *sourceTime* representa una fecha posterior al 23:59:59 de enero de 2038, UTC.

- Si usa **_ctime64_s** o **_wctime64_s** y *sourceTime* representa una fecha posterior al 23:59:59 de diciembre de 3000, hora UTC.

- Si usa **_ctime_s** o **_wctime_s**, estas funciones son contenedores para las funciones anteriores. Consulte la sección Comentarios.

*numberOfElements*<br/>
Tamaño del búfer.

*sourceTime*<br/>
Puntero a la hora almacenada.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto. Si hay un error debido a un parámetro no válido, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, se devuelve un código de error. Los códigos de error se definen en ERRNO.H; para obtener una lista de estos errores, consulte [errno](../../c-runtime-library/errno-constants.md). Los códigos de error reales generados para cada condición de error se muestran en la tabla siguiente.

## <a name="error-conditions"></a>Condiciones de error

|*búfer*|*numberOfElements*|*sourceTime*|Valor devuelto|Valor en *búfer*|
|--------------|------------------------|------------|------------|-----------------------|
|**ACEPTA**|cualquiera|cualquiera|**EINVAL**|No modificado|
|Not **null** (apunta a la memoria válida)|0|cualquiera|**EINVAL**|No modificado|
|No **null**|0< tamaño < 26|cualquiera|**EINVAL**|cadena vacía.|
|No **null**|>= 26|NULL|**EINVAL**|cadena vacía.|
|No **null**|>= 26|< 0|**EINVAL**|cadena vacía.|

## <a name="remarks"></a>Observaciones

La función **ctime_s** convierte un valor de hora almacenado como una estructura de [time_t](../../c-runtime-library/standard-types.md) en una cadena de caracteres. El valor *sourceTime* se suele obtener de una llamada a [Time](time-time32-time64.md), que devuelve el número de segundos transcurridos desde la medianoche (00:00:00) del 1 de enero de 1970, hora universal coordinada (UTC). La cadena del valor devuelto contiene exactamente 26 caracteres y tiene el formato:

`Wed Jan 02 02:03:55 1980\n\0`

Se usa un reloj de 24 horas. Todos los campos tienen un ancho constante. El carácter de nueva línea ("\n") y el carácter nulo ("\0") ocupan las dos últimas posiciones de la cadena.

La cadena de caracteres convertidos también se ajusta en función de la configuración de zona horaria local. Vea las funciones [Time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)y [localtime32_s](localtime-s-localtime32-s-localtime64-s.md) para obtener información sobre la configuración de la hora local y la función [_tzset](tzset.md) para obtener información sobre cómo definir el entorno de zona horaria y las variables globales.

**_wctime32_s** y **_wctime64_s** son la versión con caracteres anchos de **_ctime32_s** y **_ctime64_s**; devolver un puntero a una cadena de caracteres anchos. De lo contrario, **_ctime64_s**, **_wctime32_s**y **_wctime64_s** se comportan de manera idéntica a **_ctime32_s**.

**ctime_s** es una función insertada que se evalúa como **_ctime64_s** y **time_t** es equivalente a **__time64_t**. Si necesita forzar al compilador a interpretar **time_t** como la **time_t**de 32 bits anterior, puede definir **_USE_32BIT_TIME_T**. Esto hará que **ctime_s** se evalúe como **_ctime32_s**. Esto no es recomendable porque puede producir un error en la aplicación después del 18 de enero de 2038 y no se permite en plataformas de 64 bits.

En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

Las versiones de la biblioteca de depuración de estas funciones rellenan primero el búfer con 0xFE. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime_s**|**ctime_s**|**ctime_s**|**_wctime_s**|
|**_tctime32_s**|**_ctime32_s**|**_ctime32_s**|**_wctime32_s**|
|**_tctime64_s**|**_ctime64_s**|**_ctime64_s**|**_wctime64_s**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**ctime_s**, **_ctime32_s**, **_ctime64_s**|\<time.h>|
|**_wctime_s**, **_wctime32_s**, **_wctime64_s**|\<time.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_wctime_s.c
// This program gets the current
// time in time_t form and then uses _wctime_s to
// display the time in string form.

#include <time.h>
#include <stdio.h>

#define SIZE 26

int main( void )
{
   time_t ltime;
   wchar_t buf[SIZE];
   errno_t err;

   time( &ltime );

   err = _wctime_s( buf, SIZE, &ltime );
   if (err != 0)
   {
      printf("Invalid Arguments for _wctime_s. Error Code: %d\n", err);
   }
   wprintf_s( L"The time is %s\n", buf );
}
```

```Output
The time is Fri Apr 25 13:03:39 2003
```

## <a name="see-also"></a>Consulte también

[Administración de hora](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
