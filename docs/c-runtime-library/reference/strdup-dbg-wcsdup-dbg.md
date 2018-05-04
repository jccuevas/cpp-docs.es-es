---
title: _strdup_dbg, _wcsdup_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _strdup_dbg
- _wcsdup_dbg
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
- _wcsdup_dbg
- strdup_dbg
- _strdup_dbg
- wcsdup_dbg
dev_langs:
- C++
helpviewer_keywords:
- _wcsdup_dbg function
- stdup_dbg function
- copying strings
- duplicating strings
- strings [C++], copying
- strings [C++], duplicating
- _strdup_dbg function
- wcsdup_dbg function
ms.assetid: 681db70c-d124-43ab-b83e-5eeea9035097
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0e4a4791092b93d04b06432a5294a11200ed879
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="strdupdbg-wcsdupdbg"></a>_strdup_dbg, _wcsdup_dbg

Versiones de [_strdup y _wcsdup](strdup-wcsdup-mbsdup.md) que usan la versión de depuración **malloc**.

## <a name="syntax"></a>Sintaxis

```C
char *_strdup_dbg(
   const char *strSource,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wcsdup_dbg(
   const wchar_t *strSource,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parámetros

*strSource*<br/>
Cadena de origen terminada en NULL.

*blockType*<br/>
Tipo de bloque de memoria solicitado: **_CLIENT_BLOCK** o **_NORMAL_BLOCK**.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o NULL.

*linenumber*<br/>
Número de línea del archivo de código fuente en la que se solicitó la operación de asignación o valor NULL.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero a la ubicación de almacenamiento para la cadena copiada o **NULL** si no se puede asignar almacenamiento.

## <a name="remarks"></a>Comentarios

El **_strdup_dbg** y **_wcsdup_dbg** funciones son idénticas a **_strdup** y **_wcsdup** salvo que, cuando **_ DEPURAR** está definido, estas funciones usan la versión de depuración **malloc**, **_malloc_dbg**, para asignar memoria para la cadena duplicada. Para obtener información sobre las características de depuración de **_malloc_dbg**, consulte [_malloc_dbg](malloc-dbg.md).

En la mayoría de los casos, no es necesario llamar a estas funciones explícitamente en la mayoría. En su lugar, puede definir la marca **_CRTDBG_MAP_ALLOC**. Cuando **_CRTDBG_MAP_ALLOC** está definido, las llamadas a **_strdup** y **_wcsdup** se reasignan a **_strdup_dbg** y **_ wcsdup_dbg**, respectivamente, con el *existen* establecido en **_NORMAL_BLOCK**. Por lo tanto, no es necesario llamar a estas funciones explícitamente a menos que desee marcar los bloques del montón como **_CLIENT_BLOCK**. Para obtener más información sobre los tipos de bloques, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsdup_dbg**|**_strdup_dbg**|**_mbsdup**|**_wcsdup_dbg**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_strdup_dbg**, **_wcsdup_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdup, _wcsdup, _mbsdup](strdup-wcsdup-mbsdup.md)<br/>
[Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
