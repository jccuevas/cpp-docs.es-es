---
title: _getcwd_dbg, _wgetcwd_dbg
ms.date: 11/04/2016
api_name:
- _wgetcwd_dbg
- _getcwd_dbg
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 3eb318b9b2faa8716abdd26eafa926c8072b5614
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955278"
---
# <a name="_getcwd_dbg-_wgetcwd_dbg"></a>_getcwd_dbg, _wgetcwd_dbg

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
Longitud máxima de la ruta de acceso en caracteres: **Char** para **_getcwd_dbg** y **wchar_t** para **_wgetcwd_dbg**.

*blockType*<br/>
Tipo solicitado del bloque de memoria: _ **client_block** o **_NORMAL_BLOCK**.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o **null**.

*linenumber*<br/>
Número de línea del archivo de código fuente donde se solicitó la operación de asignación o **null**.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero al *búfer*. Un valor devuelto **null** indica un error y **errno** se establece en **ENOMEM**, lo que indica que no hay memoria suficiente para asignar *Maxlen* bytes (cuando se proporciona un argumento **null** como *buffer*) o a **ERANGE** , que indica que la ruta de acceso tiene más de *Maxlen* caracteres.

Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Las funciones **_getcwd_dbg** y **_wgetcwd_dbg** son idénticas **a _getcwd** y **_wgetcwd** , salvo que, cuando se define **_ Debug** , estas funciones usan la versión de depuración de **malloc** y **_ malloc_dbg** para Asigne memoria si se pasa **null** como primer parámetro. Para obtener más información, consulte [_malloc_dbg](malloc-dbg.md).

En la mayoría de los casos, no es necesario llamar a estas funciones explícitamente en la mayoría. En su lugar, puede definir la marca _ **crtdbg_map_alloc** . Cuando se define _ **crtdbg_map_alloc** , las llamadas a **_getcwd** y **_wgetcwd** se reasignan a **_getcwd_dbg** y **_Wgetcwd_dbg**, respectivamente, con el *blockType* establecido en **_NORMAL_BLOCK**. Por lo tanto, no es necesario llamar a estas funciones explícitamente a menos que desee marcar los bloques del montón como _ **client_block**. Para obtener más información, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).

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
