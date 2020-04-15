---
title: strerror, _strerror, _wcserror, __wcserror
description: Describe las funciones de Microsoft C Runtime Library (CRT) strerror, _strerror, _wcserror y __wcserror.
ms.date: 4/2/2020
api_name:
- strerror
- _strerror
- _wcserror
- __wcserror
- _o___wcserror
- _o__strerror
- _o__wcserror
- _o_strerror
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 9eecb7376cf476f0128dc20c8884746a3b4d47d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337326"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Obtiene una cadena de mensaje de error del sistema (**strerror**, **_wcserror**) o da formato a una cadena de mensaje de error proporcionada por el usuario (**_strerror**, **__wcserror**). Hay disponibles versiones más seguras de estas funciones; vea [strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

## <a name="syntax"></a>Sintaxis

```C
char * strerror(
   int errnum );

char * _strerror(
   const char *strErrMsg );

wchar_t * _wcserror(
   int errnum );

wchar_t * __wcserror(
   const wchar_t *strErrMsg );
```

### <a name="parameters"></a>Parámetros

*errnum*\
Número de error.

*strErrMsg*\
Mensaje proporcionado por el usuario.

## <a name="return-value"></a>Valor devuelto

Todas estas funciones devuelven un puntero a una cadena de mensaje de error, en un búfer de almacenamiento local de subprocesos propiedad del tiempo de ejecución. Las llamadas posteriores en el mismo subproceso pueden sobrescribir esta cadena.

## <a name="remarks"></a>Observaciones

La función **strerror** asigna *errnum* a una cadena de mensaje de error y devuelve un puntero a la cadena. Las funciones **strerror** y **_strerror** no imprimen realmente el mensaje. Para imprimir, llame a una función de salida como [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile", 2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Si *strErrMsg* se pasa como **NULL**, **_strerror** devuelve un puntero a una cadena. Contiene el mensaje de error del sistema para la última llamada de biblioteca que produjo un error. La cadena del mensaje de error termina con el carácter de línea nueva ('\n'). Cuando *strErrMsg* no es **NULL**, la cadena contiene, en orden: la cadena *strErrMsg,* dos puntos, un espacio, el mensaje de error del sistema y un carácter de nueva línea. El mensaje de cadena puede tener, como máximo, 94 caracteres de longitud, en caracteres estrechos **(_strerror)** o anchos **(__wcserror).**

El número de error real de **_strerror** se almacena en la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Para producir resultados precisos, llame a **_strerror** inmediatamente después de que una rutina de biblioteca devuelva un error. De lo contrario, las llamadas posteriores a rutinas de biblioteca pueden sobrescribir el valor **errno.**

**_wcserror** y **__wcserror** son versiones de caracteres anchos de **strerror** y **_strerror**, respectivamente.

**_strerror**, **_wcserror**y **__wcserror** son específicos de Microsoft, no parte de la biblioteca Estándar de C. No recomendamos que los use donde desee código portátil. Para la compatibilidad con C estándar, utilice **strerror** en su lugar.

Para obtener cadenas de error, se recomienda **strerror** o **_wcserror** en lugar de las macros en desuso [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) y [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) y las funciones internas en desuso **__sys_errlist** y **__sys_nerr**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones rutinarias de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror**, **__wcserror**|\<string.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [perror](perror-wperror.md).

## <a name="see-also"></a>Consulte también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)\
[más claro](clearerr.md)\
[ferror](ferror.md)\
[perror, _wperror](perror-wperror.md)
