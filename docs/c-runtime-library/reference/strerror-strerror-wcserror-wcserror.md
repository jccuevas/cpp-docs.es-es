---
title: strerror, _strerror, _wcserror, __wcserror
ms.date: 11/04/2016
api_name:
- strerror
- _strerror
- _wcserror
- __wcserror
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 0b4d70687bc2f428162d035c80d6bc8525a8fb9e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958145"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Obtiene una cadena de mensaje de error del sistema (**strerror**, **wcserror**) o da formato a una cadena de mensaje de error proporcionada por el usuario ( **_strerror**, **__wcserror**). Hay disponibles versiones más seguras de estas funciones; vea [strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

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

La función **strerror** asigna *elementos errnum* a una cadena de mensaje de error y devuelve un puntero a la cadena. Ni **strerror** ni **_strerror** imprimen realmente el mensaje: Para ello, debe llamar a una función de salida como [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Si *strErrMsg* se pasa como **null**, **_strerror** devuelve un puntero a una cadena que contiene el mensaje de error del sistema para la última llamada de biblioteca que generó un error. La cadena del mensaje de error termina con el carácter de línea nueva ('\n'). Si *strErrMsg* no es igual a **null**, **_strerror** devuelve un puntero a una cadena que contiene (en orden) el mensaje de cadena, un signo de dos puntos, un espacio, el mensaje de error del sistema para la última llamada de biblioteca que produce un error y una nueva línea óptico. El mensaje de cadena puede tener, como máximo, 94 caracteres.

El número de error real de **_strerror** se almacena en la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Para generar resultados precisos, llame a **_strerror** inmediatamente después de que una rutina de biblioteca devuelva un error. De lo contrario, las llamadas subsiguientes a **strerror** o **_strerror** pueden sobrescribir el valor **errno** .

**wcserror** y **__wcserror** son versiones de caracteres anchos de **strerror** y **_strerror**, respectivamente.

**_strerror**, **wcserror**y **__wcserror** no forman parte de la definición de ANSI; son extensiones de Microsoft y se recomienda no utilizarlas donde quiera código portable. Para la compatibilidad con ANSI, use **strerror** en su lugar.

Para obtener cadenas de error, se recomienda **strerror** o **wcserror** en lugar de las macros desusadas [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) y [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) y las funciones internas desusadas **__sys_errlist** y **__sys_nerr**.

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
