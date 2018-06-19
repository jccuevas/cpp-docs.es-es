---
title: _getdcwd, _wgetdcwd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _getdcwd
- _wgetdcwd
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wgetdcwd
- getdcwd
- _getdcwd
- tgetdcwd
- _wgetdcwd
- _tgetdcwd
dev_langs:
- C++
helpviewer_keywords:
- wgetdcwd function
- working directory
- getdcwd function
- _getdcwd function
- _wgetdcwd function
- current working directory
- directories [C++], current working
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0ccc526b196982402ca3b795276df8c790ad35a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404261"
---
# <a name="getdcwd-wgetdcwd"></a>_getdcwd, _wgetdcwd

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

*Unidad*<br/>
Entero no negativo que especifica la unidad (0 = unidad predeterminada, 1 = A, 2 = B, etc.).

Si la unidad especificada no está disponible, o no se puede determinar la clase de unidad (por ejemplo, extraíble, fija, CD-ROM, disco RAM o unidad de red), se invoca el controlador de parámetros no válidos, como se describe en [Parameter Validation](../../c-runtime-library/parameter-validation.md).

*buffer*<br/>
Ubicación de almacenamiento de la ruta de acceso o **NULL**.

Si **NULL** se especifica, esta función asigna un búfer de al menos *maxlen* tamaño mediante el uso de **malloc**y el valor devuelto de **_getdcwd**es un puntero al búfer asignado. El búfer se puede liberar llamando a **libre** y pasándole el puntero.

*MAXLEN*<br/>
Un entero positivo distinto de cero que especifica la longitud máxima de la ruta de acceso en caracteres: **char** para **_getdcwd** y **wchar_t** para **el _wgetdcwd**.

Si *maxlen* no es mayor que cero, el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md), se invoca.

## <a name="return-value"></a>Valor devuelto

Puntero a una cadena que representa la ruta de acceso completa del directorio de trabajo actual en la unidad especificada, o **NULL**, lo que indica un error.

Si *búfer* se especifica como **NULL** y no hay memoria suficiente para asignar *maxlen* caracteres, se produce un error y **errno** es establecido en **ENOMEM**. Si supera la longitud de la ruta de acceso, que incluye el carácter nulo de terminación, *maxlen*, se produce un error y **errno** está establecido en **ERANGE**. Para obtener más información sobre estos códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_getdcwd** función obtiene la ruta de acceso completa del directorio de trabajo actual en la unidad especificada y almacena en *búfer*. Si el directorio de trabajo actual es la raíz, la cadena finaliza con una barra diagonal inversa (\\). Si el directorio de trabajo actual es un directorio distinto de la raíz, la cadena finaliza con el nombre de directorio y no con una barra diagonal inversa.

**_wgetdcwd** es una versión con caracteres anchos de **_getdcwd**y su *búfer* parámetro y valor devuelto son cadenas de caracteres anchos. En caso contrario, **_wgetdcwd** y **_getdcwd** se comportan exactamente igual.

Esta función es segura para subprocesos a pesar de que depende de **GetFullPathName**, que sí misma no es segura para subprocesos. Sin embargo, la seguridad para subprocesos podría ponerse en riesgo si la aplicación multiproceso llama a esta función y a **GetFullPathName**. Para obtener más información, vaya a [MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542) y busque **GetFullPathName**.

La versión de esta función con el **_nolock** sufijo se comporta igual que esta función salvo que no es segura para subprocesos y no está protegida contra interferencias de otros subprocesos. Para obtener más información, vea [_getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md).

Cuando **_DEBUG** y **_CRTDBG_MAP_ALLOC** se definen, las llamadas a **_getdcwd** y **_wgetdcwd** se reemplazan por llamadas a **_getdcwd_dbg** y **_wgetdcwd_dbg** para que puedan depurar las asignaciones de memoria. Para obtener más información, vea [_getdcwd_dbg, _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<direct.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_getdrive](getdrive.md).

## <a name="see-also"></a>Vea también

[Control de directorio](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
