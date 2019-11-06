---
title: _strdate_s, _wstrdate_s
description: _strdate_s y _wstrdate_s son versiones de CRT seguras de las funciones _strdate y _wstrdate que colocan la fecha actual en un búfer.
ms.date: 11/01/2019
api_name:
- _strdate_s
- _wstrdate_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _strdate_s
- wstrdate_s
- _wstrdate_s
- strdate_s
- _tstrdate_s
helpviewer_keywords:
- dates, copying
- tstrdate_s function
- wstrdate_s function
- _tstrdate_s function
- strdate_s function
- copying dates
- _strdate_s function
- _wstrdate_s function
ms.assetid: d41d8ea9-e5ce-40d4-864e-1ac29b455991
ms.openlocfilehash: 7d04c134fcd19753ac0cecf8cc3b87e902d92e83
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625755"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s, _wstrdate_s

Copia la fecha actual del sistema en un búfer. Estas funciones son versiones de [_strdate, _wstrdate](strdate-wstrdate.md) con mejoras de seguridad, como se describe en [características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _strdate_s(
   char *buffer,
   size_t size
);
errno_t _wstrdate_s(
   wchar_t *buffer,
   size_t size
);
template <size_t size>
errno_t _strdate_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrdate_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>Parámetros

\ de *búfer*
Un puntero a un búfer para colocar la cadena de fecha con formato.

*tamaño* \
Tamaño del búfer en unidades de carácter.

## <a name="return-value"></a>Valor devuelto

Cero si es correcta. El valor devuelto es un código de error si se produce un error. Los códigos de error se definen en ERRNO.H; consulte la tabla siguiente para ver los errores exactos generados por esta función. Para obtener más información sobre los códigos de error, vea [errno](../../c-runtime-library/errno-constants.md).

## <a name="error-conditions"></a>Condiciones de error

|*buffer*|*size*|Volver|Contenido del *búfer*|
|--------------|------------------------|------------|--------------------------|
|**NULL**|(cualquiera)|**EINVAL**|No modificado|
|Not **null** (que apunta a un búfer válido)|0|**EINVAL**|No modificado|
|Not **null** (que apunta a un búfer válido)|0 < *tamaño* < 9|**EINVAL**|Cadena vacía|
|Not **null** (que apunta a un búfer válido)|*tamaño* > = 9|0|Fecha actual con el formato especificado en la sección de comentarios|

## <a name="security-issues"></a>Problemas de seguridad

Si se pasa un valor no válido, no nulo para el *búfer* , se produce una infracción de acceso si el parámetro de *tamaño* es mayor que nueve.

Si se pasa un valor de *tamaño* mayor que el tamaño real del *búfer* , se producirá una saturación del búfer.

## <a name="remarks"></a>Comentarios

Estas funciones proporcionan versiones más seguras de **_strdate** y **_wstrdate**. La función **_strdate_s** copia la fecha actual del sistema en el búfer señalado por el *búfer*. Tiene el formato `mm/dd/yy`, donde `mm` es el mes de dos dígitos, `dd` es el día de dos dígitos y `yy` es el último de los dos dígitos del año. Por ejemplo, la cadena `12/05/99` representa el 5 de diciembre de 1999. El búfer debe tener una longitud mínima de nueve caracteres.

**_wstrdate_s** es una versión con caracteres anchos de **_strdate_s**; el argumento y el valor devuelto de **_wstrdate_s** son cadenas de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

Cuando el *búfer* es un puntero **nulo** , o el *tamaño* es inferior a nueve caracteres, se invoca el controlador de parámetros no válidos. Se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven-1. Establecen **errno** en **EINVAL** si el búfer es **null** o si el *tamaño* es menor o igual que 0. O bien, establecen **errno** en **ERANGE** si *el tamaño* es inferior a 9.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de *tamaño* . Además, pueden reemplazar automáticamente funciones no seguras con sus homólogos más recientes y seguros. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

Las versiones de la biblioteca de depuración de estas funciones rellenan primero el búfer con 0xFE. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mapping"></a>Asignación de rutina de texto genérico:

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<time.h> o \<wchar.h>|
|**_strdate_s**|\<time.h>|

## <a name="example"></a>Ejemplo

Vea el ejemplo de [time](time-time32-time64.md).

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)\
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)\
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)\
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)\
[time, _time32, _time64](time-time32-time64.md)\
[_tzset](tzset.md)
