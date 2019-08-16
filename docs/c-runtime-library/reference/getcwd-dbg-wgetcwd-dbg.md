---
title: _getcwd_dbg, _wgetcwd_dbg
ms.date: 11/04/2016
apiname:
- _wgetcwd_dbg
- _getcwd_dbg
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getcwd_dbg
- _wgetcwd_dbg
- getcwd_dbg
- wgetcwd_dbg
helpviewer_keywords:
- wgetcwd_dbg function
- working directory
- _getcwd_dbg function
- getcwd_dbg function
- current working directory
- _wgetcwd_dbg function
- directories [C++], current working
ms.assetid: 8d5d151f-d844-4aa6-a28c-1c11a22dc00d
ms.openlocfilehash: 9616c5f7e29b4f003d3943ba058d1f1a1d5adb5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287233"
---
# <a name="getcwddbg-wgetcwddbg"></a>_getcwd_dbg, _wgetcwd_dbg

Versiones de depuración de las funciones [_getcwd, _wgetcwd](getcwd-wgetcwd.md) (disponibles únicamente durante la depuración).

## <a name="syntax"></a>Sintaxis

```C
char *_getcwd_dbg(
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetcwd_dbg(
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Ubicación de almacenamiento de la ruta de acceso.

*maxlen*<br/>
Longitud máxima de la ruta de acceso en caracteres: **char** para **_getcwd_dbg** y **wchar_t** para **_wgetcwd_dbg**.

*blockType*<br/>
Tipo del bloque de memoria solicitado: **_CLIENT_BLOCK** o **_NORMAL_BLOCK**.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o **NULL**.

*linenumber*<br/>
Número de línea en el archivo de origen que se solicitó la operación de asignación o **NULL**.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a *búfer*. Un **NULL** valor devuelto indica un error, y **errno** se establece en **ENOMEM**, que indica que no hay memoria suficiente para asignar *maxlen* bytes (cuando un **NULL** argumento se asigna como *búfer*), o a **ERANGE**, que indica que la ruta de acceso es mayor que *maxlen*  caracteres.

Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_getcwd_dbg** y **_wgetcwd_dbg** funciones son idénticas a **_getcwd** y **_wgetcwd** , salvo que, cuando **_ DEPURAR** está definido, estas funciones usan la versión de depuración **malloc** y **_malloc_dbg** para asignar memoria si **NULL** se pasa como el primer parámetro. Para obtener más información, consulte [_malloc_dbg](malloc-dbg.md).

En la mayoría de los casos, no es necesario llamar a estas funciones explícitamente en la mayoría. En su lugar, puede definir la **_CRTDBG_MAP_ALLOC** marca. Cuando **_CRTDBG_MAP_ALLOC** está definido, las llamadas a **_getcwd** y **_wgetcwd** se reasignan a **_getcwd_dbg** y **_ wgetcwd_dbg**, respectivamente, con el *existen* establecido en **_NORMAL_BLOCK**. Por lo tanto, no es necesario llamar a estas funciones explícitamente a menos que desee marcar los bloques del montón como **_CLIENT_BLOCK**. Para obtener más información, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).

## <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd_dbg**|**_getcwd_dbg**|**_getcwd_dbg**|**_wgetcwd_dbg**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_getcwd_dbg**|\<crtdbg.h>|
|**_wgetcwd_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[Control de directorio](../../c-runtime-library/directory-control.md)<br/>
[Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
