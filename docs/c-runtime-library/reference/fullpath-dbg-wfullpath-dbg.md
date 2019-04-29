---
title: _fullpath_dbg, _wfullpath_dbg
ms.date: 11/04/2016
apiname:
- _wfullpath_dbg
- _fullpath_dbg
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
apitype: DLLExport
f1_keywords:
- wfullpath_dbg
- _wfullpath_dbg
- _fullpath_dbg
- fullpath_dbg
helpviewer_keywords:
- _fullpath_dbg function
- relative file paths
- absolute paths
- fullpath_dbg function
- _wfullpath_dbg function
- wfullpath_dbg function
ms.assetid: 81f72f85-07da-4f5c-866a-598e0fb03f6b
ms.openlocfilehash: b84c5b77d0a9bfb298d4c597e372cd39a92441f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332954"
---
# <a name="fullpathdbg-wfullpathdbg"></a>_fullpath_dbg, _wfullpath_dbg

Las versiones de [_fullpath, _wfullpath](fullpath-wfullpath.md) que usan la versión de depuración **malloc** para asignar memoria.

## <a name="syntax"></a>Sintaxis

```C
char *_fullpath_dbg(
   char *absPath,
   const char *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wfullpath_dbg(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parámetros

*absPath*<br/>
Puntero a un búfer que contiene el nombre de ruta de acceso absoluta o completa, o **NULL**.

*relPath*<br/>
Nombre de ruta de acceso relativa.

*maxLength*<br/>
Longitud máxima del búfer de nombre de ruta de acceso absoluta (*absPath*). Es esta longitud en bytes para **_fullpath** pero, en caracteres anchos (**wchar_t**) para **_wfullpath**.

*blockType*<br/>
Tipo de bloque de memoria solicitado: **_CLIENT_BLOCK** o **_NORMAL_BLOCK**.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o **NULL**.

*linenumber*<br/>
Número de línea en el archivo de origen que se solicitó la operación de asignación o **NULL**.

## <a name="return-value"></a>Valor devuelto

Cada función devuelve un puntero a un búfer que contiene el nombre de ruta de acceso absoluta (*absPath*). Si se produce un error (por ejemplo, si el valor pasado en *relPath* incluye una letra de unidad que no es válido o no se encuentra, o si la longitud del nombre de ruta de acceso absoluta creado (*absPath*) es mayor que *maxLength*) devuelve la función **NULL**.

## <a name="remarks"></a>Comentarios

El **_fullpath_dbg** y **_wfullpath_dbg** funciones son idénticas a **_fullpath** y **_wfullpath** , salvo que, cuando **_DEBUG** está definido, estas funciones usan la versión de depuración **malloc**, **_malloc_dbg**para asignar memoria si **NULL** se pasa como primer parámetro. Para obtener información sobre las características de depuración de **_malloc_dbg**, consulte [_malloc_dbg](malloc-dbg.md).

En la mayoría de los casos, no es necesario llamar a estas funciones explícitamente en la mayoría. En su lugar, puede definir la **_CRTDBG_MAP_ALLOC** marca. Cuando **_CRTDBG_MAP_ALLOC** está definido, las llamadas a **_fullpath** y **_wfullpath** se reasignan a **_fullpath_dbg** y **_wfullpath_dbg**, respectivamente, con el *existen* establecido en **_NORMAL_BLOCK**. Por lo tanto, no es necesario llamar a estas funciones explícitamente a menos que desee marcar los bloques del montón como **_CLIENT_BLOCK**. Para obtener más información, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath_dbg**|**_fullpath_dbg**|**_fullpath_dbg**|**_wfullpath_dbg**|

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fullpath_dbg**|\<crtdbg.h>|
|**_wfullpath_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
