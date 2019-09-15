---
title: _strdate, _wstrdate
ms.date: 11/04/2016
api_name:
- _strdate
- _wstrdate
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
- _tstrdate
- wstrdate
- _wstrdate
- _strdate
- strdate
helpviewer_keywords:
- strdate function
- dates, copying
- tstrdate function
- _wstrdate function
- wstrdate function
- _strdate function
- _tstrdate function
- copying dates
ms.assetid: de8e4097-58f8-42ba-9dcd-cb4d9a9f1696
ms.openlocfilehash: e1164db5857643bac649e96493a3d66cdee3b6e2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958217"
---
# <a name="_strdate-_wstrdate"></a>_strdate, _wstrdate

Copia la fecha actual del sistema en un búfer. Hay disponibles versiones más seguras de estas funciones; vea [_strdate_s, _wstrdate_s](strdate-s-wstrdate-s.md).

## <a name="syntax"></a>Sintaxis

```C
char *_strdate(
   char *datestr
);
wchar_t *_wstrdate(
   wchar_t *datestr
);
template <size_t size>
char *_strdate(
   char (&datestr)[size]
); // C++ only
template <size_t size>
wchar_t *_wstrdate(
   wchar_t (&datestr)[size]
); // C++ only
```

### <a name="parameters"></a>Parámetros

*datestr*<br/>
Puntero a un búfer que contiene la cadena de fecha con formato.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero a la cadena de caracteres resultante *datestr*.

## <a name="remarks"></a>Comentarios

Hay disponibles versiones más seguras de estas funciones; vea [_strdate_s, _wstrdate_s](strdate-s-wstrdate-s.md). Se recomienda usar siempre que sea posible las funciones más seguras.

La función **_strdate** copia la fecha actual del sistema en el búfer señalado por *datestr*, con formato **mm**/**DD**/**AA**, donde **mm** es dos dígitos que representan el mes, **DD** es dos dígitos que representan el día y **YY** son los dos últimos dígitos del año. Por ejemplo, la cadena **12/05/99** representa el 5 de diciembre de 1999. La longitud del búfer debe ser de 9 bytes como mínimo.

Si *datestr* es un puntero **nulo** , se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven-1 y establecen **errno** en **EINVAL**.

**_wstrdate** es una versión con caracteres anchos de **_strdate**; el argumento y el valor devuelto de **_wstrdate** son cadenas de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

En C++, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate**|**_strdate**|**_strdate**|**_wstrdate**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<time.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// strdate.c
// compile with: /W3
#include <time.h>
#include <stdio.h>
int main()
{
    char tmpbuf[9];

    // Set time zone from TZ environment variable. If TZ is not set,
    // the operating system is queried to obtain the default value
    // for the variable.
    //
    _tzset();

    printf( "OS date: %s\n", _strdate(tmpbuf) ); // C4996
    // Note: _strdate is deprecated; consider using _strdate_s instead
}
```

```Output
OS date: 04/25/03
```

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
