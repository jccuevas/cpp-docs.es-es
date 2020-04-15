---
title: _strdate_s, _wstrdate_s
description: _strdate_s y _wstrdate_s son versiones seguras de CRT de las funciones _strdate y _wstrdate que colocan la fecha actual en un búfer.
ms.date: 4/2/2020
api_name:
- _strdate_s
- _wstrdate_s
- _o__strdate_s
- _o__wstrdate_s
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
ms.openlocfilehash: b4d977ba3546eae17218c63b1786fd26c784d340
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359824"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s, _wstrdate_s

Copia la fecha actual del sistema en un búfer. Estas funciones son versiones de [_strdate, _wstrdate](strdate-wstrdate.md) con mejoras de seguridad como se describe en Características de seguridad [en el CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Búfer*\
Puntero a un búfer para colocar la cadena de fecha con formato.

*Tamaño*\
Tamaño del búfer en unidades de caracteres.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto. El valor devuelto es un código de error si se produce un error. Los códigos de error se definen en ERRNO.H; consulte la tabla siguiente para ver los errores exactos generados por esta función. Para obtener más información sobre los códigos de error, vea [errno](../../c-runtime-library/errno-constants.md).

## <a name="error-conditions"></a>Condiciones del error

|*Búfer*|*Tamaño*|Valor devuelto|Contenido del *búfer*|
|--------------|------------------------|------------|--------------------------|
|**Null**|(cualquiera)|**EINVAL**|No modificado|
|No **NULL** (apuntando al búfer válido)|0|**EINVAL**|No modificado|
|No **NULL** (apuntando al búfer válido)|0 < *tamaño* < 9|**EINVAL**|cadena vacía.|
|No **NULL** (apuntando al búfer válido)|*tamaño* >9|0|Fecha actual con el formato especificado en la sección de comentarios|

## <a name="security-issues"></a>Problemas de seguridad

Si se pasa un valor no válido y no NULL para el *búfer,* se produce una infracción de acceso si el parámetro *size* es mayor que nueve.

Si se pasa un valor para un *tamaño* mayor que el tamaño real del *búfer,* se satura una saturación del búfer.

## <a name="remarks"></a>Observaciones

Estas funciones proporcionan versiones más seguras de **_strdate** y **_wstrdate.** La función **_strdate_s** copia la fecha actual del sistema en el búfer al que apunta *el búfer.* Está `mm/dd/yy`formateado, `mm` donde está el `dd` mes de dos dígitos, es el día de dos dígitos y `yy` es los dos últimos dígitos del año. Por ejemplo, la cadena `12/05/99` representa el 5 de diciembre de 1999. El búfer debe tener al menos nueve caracteres.

**_wstrdate_s** es una versión de caracteres anchos de **_strdate_s;** el argumento y el valor devuelto de **_wstrdate_s** son cadenas de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

Cuando *buffer* es un puntero **NULL,** o *el tamaño* es inferior a nueve caracteres, se invoca el controlador de parámetros no válidos. Se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1. Establecen **errno en** **EINVAL** si el búfer es **NULL** o si *el tamaño* es menor o igual que 0. O bien, establecen **errno en** **ERANGE** si el *tamaño* es menor que 9.

En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento *de tamaño.* Además, pueden reemplazar automáticamente las funciones no seguras con sus contrapartes más nuevas y seguras. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

Las versiones de la biblioteca de depuración de estas funciones rellenan primero el búfer con 0xFE. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

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

## <a name="see-also"></a>Consulte también

[Gestión del tiempo](../../c-runtime-library/time-management.md)\
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)\
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)\
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)\
[tiempo, _time32, _time64](time-time32-time64.md)\
[_tzset](tzset.md)
