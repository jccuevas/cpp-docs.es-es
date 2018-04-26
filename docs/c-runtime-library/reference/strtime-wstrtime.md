---
title: _strtime, _wstrtime | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wstrtime
- _strtime
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
- _wstrtime
- _strtime
- wstrtime
- strtime
- _tstrtime
dev_langs:
- C++
helpviewer_keywords:
- strtime function
- _strtime function
- _wstrtime function
- copying time to buffers
- wstrtime function
- tstrtime function
- _tstrtime function
- time, copying
ms.assetid: 9e538161-cf49-44ec-bca5-c0ab0b9e4ca3
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2533fa8e3c60cbecbf4ab04c4f2508ef225b62a3
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="strtime-wstrtime"></a>_strtime, _wstrtime

Copia la hora en un búfer. Hay disponibles versiones más seguras de estas funciones; vea [_strtime_s, _wstrtime_s](strtime-s-wstrtime-s.md).

## <a name="syntax"></a>Sintaxis

```C
char *_strtime(
   char *timestr
);
wchar_t *_wstrtime(
   wchar_t *timestr
);
template <size_t size>
char *_strtime(
   char (&timestr)[size]
); // C++ only
template <size_t size>
wchar_t *_wstrtime(
   wchar_t (&timestr)[size]
); // C++ only
```

### <a name="parameters"></a>Parámetros

*timestr*<br/>
Cadena de hora.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la cadena de caracteres resultante *timestr*.

## <a name="remarks"></a>Comentarios

El **_strtime** función copia la hora local actual en el búfer señalado por *timestr*. La hora se formatea como **hh** donde **hh** es de dos dígitos que representa la hora en la notación de 24 horas, **mm** es de dos dígitos que representa los minutos transcurridos tras la hora y **ss** es de dos dígitos que representa los segundos. Por ejemplo, la cadena **18:23:44** representa 23 minutos y 44 segundos más allá de 6 p. M. La longitud del búfer debe ser de 9 bytes como mínimo.

**_wstrtime** es una versión con caracteres anchos de **_strtime**; el argumento y el valor devuelto de **_wstrtime** son cadenas de caracteres anchos. Estas funciones se comportan exactamente igual. Si *timestr* es **NULL** puntero o si *timestr* tiene un formato incorrecto, no válido se invoca el controlador de parámetros, como se describe en [parámetro Validación](../../c-runtime-library/parameter-validation.md). Si la excepción puede continuar, estas funciones devuelven un valor NULL y el conjunto **errno** a **EINVAL** si *timestr* era un valor NULL o establecer **errno**a **ERANGE** si *timestr* tiene un formato incorrecto.

En C++, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime**|**_strtime**|**_strtime**|**_wstrtime**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_strtime**|\<time.h>|
|**_wstrtime**|\<time.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_strtime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
   char tbuffer [9];
   _strtime( tbuffer ); // C4996
   // Note: _strtime is deprecated; consider using _strtime_s instead
   printf( "The current time is %s \n", tbuffer );
}
```

```Output
The current time is 14:21:44
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
