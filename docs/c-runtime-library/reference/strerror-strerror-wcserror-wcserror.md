---
title: strerror, _strerror, _wcserror, __wcserror
description: Describe las funciones de la biblioteca en tiempo de ejecución de Microsoft C (CRT) strerror, _strerror, _wcserror y __wcserror.
ms.date: 01/07/2020
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
ms.openlocfilehash: 8c9c6850d6620407897b2a3a1dbf32e61f6719c0
ms.sourcegitcommit: 7bd3567fc6a0e7124aab51cad63bbdb44a99a848
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755045"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Obtiene una cadena de mensaje de error del sistema (**strerror**, **_wcserror**) o da formato a una cadena de mensaje de error proporcionada por el usuario ( **_strerror**, **__wcserror**). Hay disponibles versiones más seguras de estas funciones; vea [strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

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

### <a name="parameters"></a>Parameters

\ *elementos errnum*
Número de error.

\ *strErrMsg*
Mensaje proporcionado por el usuario.

## <a name="return-value"></a>Valor devuelto

Todas estas funciones devuelven un puntero a una cadena de mensaje de error, en un búfer de almacenamiento local de subprocesos propiedad del tiempo de ejecución. Las llamadas posteriores en el mismo subproceso pueden sobrescribir esta cadena.

## <a name="remarks"></a>Notas

La función **strerror** asigna *elementos errnum* a una cadena de mensaje de error y devuelve un puntero a la cadena. Las funciones **strerror** y **_strerror** no imprimen realmente el mensaje. Para imprimir, llame a una función de salida como [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile", 2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Si *strErrMsg* se pasa como **null**, **_strerror** devuelve un puntero a una cadena. Contiene el mensaje de error del sistema de la última llamada de biblioteca que generó un error. La cadena del mensaje de error termina con el carácter de línea nueva ('\n'). Cuando *strErrMsg* no es **null**, la cadena contiene, en orden: la cadena *strErrMsg* , dos puntos, un espacio, el mensaje de error del sistema y un carácter de nueva línea. El mensaje de cadena puede tener, como máximo, 94 caracteres de longitud, en caracteres estrechos ( **_strerror**) o anchos ( **__wcserror**).

El número de error real de **_strerror** se almacena en la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Para generar resultados precisos, llame a **_strerror** inmediatamente después de que una rutina de biblioteca devuelva un error. De lo contrario, las llamadas posteriores a las rutinas de biblioteca pueden sobrescribir el valor **errno** .

**_wcserror** y **__wcserror** son versiones con caracteres anchos de **strerror** y **_strerror**, respectivamente.

**_strerror**, **_wcserror**y **__wcserror** son específicos de Microsoft, no forman parte de la biblioteca estándar de C. No se recomienda usarlas donde quiera código portable. Para la compatibilidad estándar de C, use **strerror** en su lugar.

Para obtener cadenas de error, se recomienda **strerror** o **_wcserror** en lugar de las macros en [desuso _sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) y [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) y las funciones internas en desuso **__sys_errlist** y **__sys_nerr**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>Requisitos de

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror**, **__wcserror**|\<string.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [perror](perror-wperror.md).

## <a name="see-also"></a>Vea también

\ de [manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)
[clearerr](clearerr.md)\
[ferror](ferror.md)\
[perror, _wperror](perror-wperror.md)
