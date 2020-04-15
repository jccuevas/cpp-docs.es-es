---
title: _getdcwd, _wgetdcwd
ms.date: 4/2/2020
api_name:
- _getdcwd
- _wgetdcwd
- _o__getdcwd
- _o__wgetdcwd
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wgetdcwd
- getdcwd
- _getdcwd
- tgetdcwd
- _wgetdcwd
- _tgetdcwd
helpviewer_keywords:
- wgetdcwd function
- working directory
- getdcwd function
- _getdcwd function
- _wgetdcwd function
- current working directory
- directories [C++], current working
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
ms.openlocfilehash: 3a4ca8ff3f1153893282c65bc4c2becd687138ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344397"
---
# <a name="_getdcwd-_wgetdcwd"></a>_getdcwd, _wgetdcwd

Obtiene la ruta de acceso completa del directorio de trabajo actual en la unidad especificada.

## <a name="syntax"></a>Sintaxis

```C
char *_getdcwd(
   int drive,
   char *buffer,
   int maxlen
);
wchar_t *_wgetdcwd(
   int drive,
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>Parámetros

*Conducir*<br/>
Entero no negativo que especifica la unidad (0 = unidad predeterminada, 1 = A, 2 = B, etc.).

Si la unidad especificada no está disponible o no se puede determinar el tipo de unidad (por ejemplo, extraíble, fijo, CD-ROM, disco RAM o unidad de red), se invoca el controlador de parámetros no válidos. Para más información, consulte [Validación de parámetros](../../c-runtime-library/parameter-validation.md).

*Búfer*<br/>
Ubicación de almacenamiento de la ruta de acceso o **NULL**.

Si se especifica **NULL,** esta función asigna un búfer de al menos *maxlen* size mediante **malloc**y el valor devuelto de **_getdcwd** es un puntero al búfer asignado. El búfer se puede liberar llamando a **free** y pasándole el puntero.

*maxlen*<br/>
Entero positivo distinto de cero que especifica la longitud máxima de la ruta de acceso, en caracteres: **char** para **_getdcwd** y **wchar_t** para **_wgetdcwd**.

Si *maxlen* es menor o igual que cero, se invoca el controlador de parámetros no válidos. Para más información, consulte [Validación de parámetros](../../c-runtime-library/parameter-validation.md).

## <a name="return-value"></a>Valor devuelto

Puntero a una cadena que representa la ruta de acceso completa del directorio de trabajo actual en la unidad especificada, o **NULL**, lo que indica un error.

Si el *búfer* se especifica como **NULL** y no hay memoria suficiente para asignar caracteres *maxlen,* se produce un error y **errno** se establece en **ENOMEM**. Si la longitud de la ruta de acceso, incluido el carácter nulo de terminación, supera *maxlen*, se produce un error y **errno** se establece en **ERANGE**. Para obtener más información sobre estos códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **_getdcwd** obtiene la ruta de acceso completa del directorio de trabajo actual en la unidad especificada y la almacena en el *búfer.* Si el directorio de trabajo actual es la raíz, la cadena finaliza con una barra diagonal inversa (\\). Si el directorio de trabajo actual es un directorio distinto de la raíz, la cadena finaliza con el nombre de directorio y no con una barra diagonal inversa.

**_wgetdcwd** es una versión de caracteres anchos de **_getdcwd**, y su parámetro *de búfer* y el valor devuelto son cadenas de caracteres anchos. De lo contrario, **_wgetdcwd** y **_getdcwd** comportarse de forma idéntica.

Esta función es segura para subprocesos a pesar de que depende de **GetFullPathName**, que sí misma no es segura para subprocesos. Sin embargo, la seguridad para subprocesos podría ponerse en riesgo si la aplicación multiproceso llama a esta función y a [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamew).

La versión de esta función que tiene **el** _nolock sufijo se comporta de forma idéntica a esta función, excepto que no es segura para subprocesos y no está protegida contra interferencias de otros subprocesos. Para obtener más información, vea [_getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md).

Cuando se definen **_DEBUG** y **_CRTDBG_MAP_ALLOC,** las llamadas a **_getdcwd** y **_wgetdcwd** se reemplazan por llamadas a **_getdcwd_dbg** y **_wgetdcwd_dbg** para que pueda depurar las asignaciones de memoria. Para obtener más información, consulte[_getdcwd_dbg, _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<direct.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_getdrive](getdrive.md).

## <a name="see-also"></a>Consulte también

[Control de directorio](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
