---
title: _strdate_s, _wstrdate_s
ms.date: 11/04/2016
apiname:
- _strdate_s
- _wstrdate_s
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
ms.openlocfilehash: 85c9ab7dcad68f3aa4832236461cd38b07d4ae44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353994"
---
# <a name="strdates-wstrdates"></a>_strdate_s, _wstrdate_s

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

|*buffer*|*numberOfElements*|Volver|Contenido de *búfer*|
|--------------|------------------------|------------|--------------------------|
|**NULL**|(cualquiera)|**EINVAL**|No modificado|
|No **NULL** (apunta al búfer válido)|0|**EINVAL**|No modificado|
|No **NULL** (apunta al búfer válido)|0 < *numberOfElements* < 9|**EINVAL**|Cadena vacía|
|No **NULL** (apunta al búfer válido)|*numberOfElements* >= 9|0|Fecha actual con el formato especificado en la sección de comentarios|

## <a name="security-issues"></a>Problemas de seguridad

Pasando un no válido no **NULL** valor para el búfer, se producirá una infracción de acceso si el *numberOfElements* parámetro es mayor que 9.

Pasar valores para el tamaño que es mayor que el tamaño real de la *búfer* dará como resultado de la saturación del búfer.

## <a name="remarks"></a>Comentarios

Estas funciones proporcionan versiones más seguras de **_strdate** y **_wstrdate**. El **_strdate_s** función copia la fecha actual del sistema en el búfer señalado por *búfer*, con el formato **mm**/**dd** / **yy**, donde **mm** son dos dígitos que representa el mes, **dd** son dos dígitos que representa el día, y **AA**  es los dos últimos dígitos del año. Por ejemplo, la cadena **05/12/99** representa 5 de diciembre de 1999. El búfer debe tener una longitud mínima de 9 caracteres.

**_wstrdate_s** es una versión con caracteres anchos de **_strdate_s**; el argumento y el valor devuelto de **_wstrdate_s** son cadenas de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

Si *búfer* es un **NULL** puntero, o si *numberOfElements* es inferior a 9 caracteres, se invoca el controlador de parámetros no válidos, como se describe en [ Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y establezca **errno** a **EINVAL** si el búfer es **NULL** o si *numberOfElements*es menor o igual que 0, o un conjunto **errno** a **ERANGE** si *numberOfElements* es inferior a 9.

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
