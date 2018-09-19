---
title: _tempnam_dbg, _wtempnam_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wtempnam_dbg
- _tempnam_dbg
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
- wtempnam_dbg
- tempnam_dbg
- _tempnam_dbg
- _wtempnam_dbg
dev_langs:
- C++
helpviewer_keywords:
- file names [C++], creating temporary
- tempnam_dbg function
- temporary files, creating
- file names [C++], temporary
- wtempnam_dbg function
- _tempnam_dbg function
- _wtempnam_dbg function
ms.assetid: e3760bb4-bb01-4808-b689-2c45af56a170
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8509d9f4b8be5771abc7dfb3d4deacc9ae61494
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412054"
---
# <a name="tempnamdbg-wtempnamdbg"></a>_tempnam_dbg, _wtempnam_dbg

Versiones de función de [_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) que usan la versión de depuración **malloc**, **_malloc_dbg**.

## <a name="syntax"></a>Sintaxis

```C
char *_tempnam_dbg(
   const char *dir,
   const char *prefix,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wtempnam_dbg(
   const wchar_t *dir,
   const wchar_t *prefix,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parámetros

*dir*<br/>
Ruta de acceso que se usa en el nombre de archivo si no hay variable de entorno TMP, o si TMP no es un directorio válido.

*Prefijo*<br/>
La cadena que se va a anteponer a nombres devueltos por **_tempnam**.

*blockType*<br/>
Tipo de bloque de memoria solicitado: **_CLIENT_BLOCK** o **_NORMAL_BLOCK**.

*filename*<br/>
Puntero al nombre de archivo de código fuente que solicitó la operación de asignación o **NULL**.

*linenumber*<br/>
Número de línea en el archivo de código fuente que se solicitó la operación de asignación o **NULL**.

## <a name="return-value"></a>Valor devuelto

Cada función devuelve un puntero al nombre generado o **NULL** si se produce un error. Error puede producirse si hay un nombre de directorio no válido especificado en la variable de entorno TMP y en el *dir* parámetro.

> [!NOTE]
> **libre** (o **free_dbg**) debe llamarse para punteros asignados por **_tempnam_dbg** y **_wtempnam_dbg**.

## <a name="remarks"></a>Comentarios

El **_tempnam_dbg** y **_wtempnam_dbg** funciones son idénticas a **_tempnam** y **_wtempnam** salvo que, cuando **_DEBUG** está definido, estas funciones usan la versión de depuración **malloc** y **_malloc_dbg**, para asignar memoria si **NULL** es se pasa como primer parámetro. Para obtener más información, consulte [_malloc_dbg](malloc-dbg.md).

En la mayoría de los casos, no es necesario llamar a estas funciones explícitamente en la mayoría. En su lugar, puede definir la marca **_CRTDBG_MAP_ALLOC**. Cuando **_CRTDBG_MAP_ALLOC** está definido, las llamadas a **_tempnam** y **_wtempnam** se reasignan a **_tempnam_dbg** y **_ wtempnam_dbg**, respectivamente, con el *existen* establecido en **_NORMAL_BLOCK**. Por lo tanto, no es necesario llamar a estas funciones explícitamente a menos que desee marcar los bloques del montón como **_CLIENT_BLOCK**. Para obtener más información, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttempnam_dbg**|**_tempnam_dbg**|**_tempnam_dbg**|**_wtempnam_dbg**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_tempnam_dbg**, **_wtempnam_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
