---
title: _strdate_s, _wstrdate_s
ms.date: 11/04/2016
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
ms.openlocfilehash: fadd30ec81cff59d675212e59c8513656c7b2f35
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940751"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s, _wstrdate_s

Copia la fecha actual del sistema en un búfer. Se trata de versiones de [_strdate, _wstrdate](strdate-wstrdate.md) que incluyen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _strdate_s(
   char *buffer,
   size_t numberOfElements
);
errno_t _wstrdate_s(
   wchar_t *buffer,
   size_t numberOfElements
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

*buffer*<br/>
Puntero a un búfer que se rellenará con la cadena de fecha con formato.

*numberOfElements*<br/>
Tamaño del búfer.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto. Si se produce un error, el valor devuelto es un código de error. Los códigos de error se definen en ERRNO.H; consulte la tabla siguiente para ver los errores exactos generados por esta función. Para obtener más información sobre los códigos de error, vea [errno](../../c-runtime-library/errno-constants.md).

## <a name="error-conditions"></a>Condiciones de error

|*buffer*|*numberOfElements*|Volver|Contenido del *búfer*|
|--------------|------------------------|------------|--------------------------|
|**NULL**|(cualquiera)|**EINVAL**|No modificado|
|Not **null** (que apunta a un búfer válido)|0|**EINVAL**|No modificado|
|Not **null** (que apunta a un búfer válido)|0 < *numberOfElements* < 9|**EINVAL**|Cadena vacía|
|Not **null** (que apunta a un búfer válido)|*numberOfElements* >= 9|0|Fecha actual con el formato especificado en la sección de comentarios|

## <a name="security-issues"></a>Problemas de seguridad

Si se pasa un valor no **null** no válido para el búfer, se producirá una infracción de acceso si el parámetro *numberOfElements* es mayor que 9.

Si se pasan valores de tamaño mayor que el tamaño real del *búfer* , se producirá una saturación del búfer.

## <a name="remarks"></a>Comentarios

Estas funciones proporcionan versiones más seguras de **_strdate** y **_wstrdate**. La **función _strdate_s** copia la fecha actual del sistema en el búfer señalado por el *búfer*, con formato **mm**/**DD**/**AA**, donde **mm** es dos dígitos que representan el mes, **DD** es dos dígitos que representan el día y **YY** son los dos últimos dígitos del año. Por ejemplo, la cadena **12/05/99** representa el 5 de diciembre de 1999. El búfer debe tener una longitud mínima de 9 caracteres.

**_wstrdate_s** es una versión con caracteres anchos de **_strdate_s**; el argumento y el valor devuelto de **_wstrdate_s** son cadenas de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

Si el *búfer* es un puntero **nulo** , o si *numberOfElements* tiene menos de 9 caracteres, se invoca el controlador de parámetros no válidos, tal y como se describe en validación de [parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven-1 y establecen **errno** en **EINVAL** si el búfer es **null** o si *numberOfElements* es menor o igual que 0, o establece **errno** en **ERANGE** si *numberOfElements* es menor que 9.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

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

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
