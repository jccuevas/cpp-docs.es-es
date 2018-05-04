---
title: strerror, _strerror, _wcserror, __wcserror | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- strerror
- _strerror
- _wcserror
- __wcserror
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __sys_errlist
- wcserror
- _strerror
- __wcserror
- strerror
- __sys_nerr
- _tcserror
- _wcserror
- tcserror
dev_langs:
- C++
helpviewer_keywords:
- strerror function
- _strerror function
- __sys_errlist
- wcserror function
- error messages, printing
- __sys_nerr
- tcserror function
- printing error messages
- _wcserror function
- _tcserror function
- __wcserror function
- error messages, getting
ms.assetid: 27b72255-f627-43c0-8836-bcda8b003e14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e89a5de45baeb9b3beea2aa538cb0a2168f3c5ed
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="strerror-strerror-wcserror-wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Obtiene una cadena de mensaje de error de sistema (**strerror**, **_wcserror**) o da formato a una cadena de mensaje de error proporcionado por el usuario (**_strerror**, **__wcserror**). Hay disponibles versiones más seguras de estas funciones; vea [strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

## <a name="syntax"></a>Sintaxis

```C
char *strerror(
   int errnum
);
char *_strerror(
   const char *strErrMsg
);
wchar_t * _wcserror(
   int errnum
);
wchar_t * __wcserror(
   const wchar_t *strErrMsg
);
```

### <a name="parameters"></a>Parámetros

*errnum*<br/>
Número de error.

*strErrMsg*<br/>
Mensaje proporcionado por el usuario.

## <a name="return-value"></a>Valor devuelto

Todas estas funciones devuelven un puntero a la cadena de mensaje de error. Las siguientes llamadas pueden sobrescribir la cadena.

## <a name="remarks"></a>Comentarios

El **strerror** función mapas *errnum* en una cadena de mensaje de error y devuelve un puntero a la cadena. Ni **strerror** ni **_strerror** imprimen realmente el mensaje: para ello, tendrá que llamar a una función de salida como [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Si *strErrMsg* se pasa como **NULL**, **_strerror** devuelve un puntero a una cadena que contiene el mensaje de error de sistema de la última llamada a biblioteca que generó un error. La cadena del mensaje de error termina con el carácter de línea nueva ('\n'). Si *strErrMsg* no es igual a **NULL**, a continuación, **_strerror** devuelve un puntero a una cadena que contiene (en orden) el mensaje de cadena, dos puntos, un espacio, el error del sistema mensaje de la última llamada a biblioteca que genera un error y un carácter de nueva línea. El mensaje de cadena puede tener, como máximo, 94 caracteres.

El número de error real para **_strerror** se almacena en la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Para generar resultados precisos, llame a **_strerror** inmediatamente después de una rutina de biblioteca devuelva un error. En caso contrario, las llamadas subsiguientes a **strerror** o **_strerror** puede sobrescribir el **errno** valor.

**_wcserror** y **__wcserror** son versiones de caracteres anchos de **strerror** y **_strerror**, respectivamente.

**_strerror**, **_wcserror**, y **__wcserror** no forman parte de la definición de ANSI; son extensiones de Microsoft y se recomienda que no usarlos donde quiere es código portable. Para la compatibilidad con ANSI, use **strerror** en su lugar.

Para obtener cadenas de error, se recomienda **strerror** o **_wcserror** en lugar de las macros en desuso [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) y [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) y las funciones internas desusadas **__sys_errlist** y **__sys_nerr**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror**, **__wcserror**|\<string.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [perror](perror-wperror.md).

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
