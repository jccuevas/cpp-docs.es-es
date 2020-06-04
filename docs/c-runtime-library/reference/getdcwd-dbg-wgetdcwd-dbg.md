---
title: _getdcwd_dbg, _wgetdcwd_dbg
ms.date: 11/04/2016
api_name:
- _getdcwd_dbg
- _wgetdcwd_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getdcwd_dbg
- getdcwd_dbg
- _wgetdcwd_dbg
- wgetdcwd_dbg
helpviewer_keywords:
- working directory
- _getdcwd_dbg function
- wgetdcwd_dbg function
- current working directory
- getdcwd_dbg function
- _wgetdcwd_dbg function
- directories [C++], current working
ms.assetid: 266bf6f0-0417-497f-963d-2e0f306d9385
ms.openlocfilehash: 8eb22f3716102c1b63b483e493eb44ac99228004
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955230"
---
# <a name="_getdcwd_dbg-_wgetdcwd_dbg"></a>_getdcwd_dbg, _wgetdcwd_dbg

Versiones de depuración de las funciones [_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md) (disponibles únicamente durante la depuración).

## <a name="syntax"></a>Sintaxis

```C
char *_getdcwd_dbg(
   int drive,
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetdcwd_dbg(
   int drive,
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parámetros

*drive*<br/>
Nombre de la unidad de disco.

*buffer*<br/>
Ubicación de almacenamiento de la ruta de acceso.

*maxlen*<br/>
Longitud máxima de la ruta de acceso en caracteres: **Char** para **_getdcwd_dbg** y **wchar_t** para **_wgetdcwd_dbg**.

*blockType*<br/>
Tipo solicitado del bloque de memoria: _ **client_block** o **_NORMAL_BLOCK**.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o **null**.

*linenumber*<br/>
Número de línea del archivo de código fuente donde se solicitó la operación de asignación o **null**.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero al *búfer*. Un valor devuelto **null** indica un error y **errno** se establece en **ENOMEM**, lo que indica que no hay memoria suficiente para asignar *Maxlen* bytes (cuando se proporciona un argumento **null** como *buffer*) o a **ERANGE** , que indica que la ruta de acceso tiene más de *Maxlen* caracteres. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Las funciones **_getdcwd_dbg** y **_wgetdcwd_dbg** son idénticas **a _getdcwd** y **_wgetdcwd** , salvo que, cuando se define **_ Debug** , estas funciones usan la versión de depuración de **malloc** y **_ malloc_dbg** para Asigne memoria si se pasa **null** como parámetro de *búfer* . Para obtener más información, consulte [_malloc_dbg](malloc-dbg.md).

En la mayoría de los casos, no es necesario llamar a estas funciones explícitamente en la mayoría. En su lugar, puede definir la marca _ **crtdbg_map_alloc** . Cuando se define _ **crtdbg_map_alloc** , las llamadas a **_getdcwd** y **_wgetdcwd** se reasignan a **_getdcwd_dbg** y **_Wgetdcwd_dbg**, respectivamente, con el *blockType* establecido en **_NORMAL_BLOCK**. Por lo tanto, no es necesario llamar a estas funciones explícitamente a menos que desee marcar los bloques del montón como _ **client_block**. Para obtener más información, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd_dbg**|**_getdcwd_dbg**|**_getdcwd_dbg**|**_wgetdcwd_dbg**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_getdcwd_dbg**|\<crtdbg.h>|
|**_wgetdcwd_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[Control de directorio](../../c-runtime-library/directory-control.md)<br/>
[Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
