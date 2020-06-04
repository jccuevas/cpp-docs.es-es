---
title: _tempnam_dbg, _wtempnam_dbg
ms.date: 11/04/2016
api_name:
- _wtempnam_dbg
- _tempnam_dbg
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
- wtempnam_dbg
- tempnam_dbg
- _tempnam_dbg
- _wtempnam_dbg
helpviewer_keywords:
- file names [C++], creating temporary
- tempnam_dbg function
- temporary files, creating
- file names [C++], temporary
- wtempnam_dbg function
- _tempnam_dbg function
- _wtempnam_dbg function
ms.assetid: e3760bb4-bb01-4808-b689-2c45af56a170
ms.openlocfilehash: 73642730995ac5c0b47519fac64b30400d47767c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946247"
---
# <a name="_tempnam_dbg-_wtempnam_dbg"></a>_tempnam_dbg, _wtempnam_dbg

Versiones de función de [_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) que usan la versión de depuración de **malloc**, **_ malloc_dbg**.

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

*prefix*<br/>
Cadena que se va a anteponer a los nombres devueltos por **_tempnam**.

*blockType*<br/>
Tipo de bloque de memoria solicitado: _ **client_block** o **_NORMAL_BLOCK**.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o **null**.

*linenumber*<br/>
Número de línea del archivo de código fuente donde se solicitó la operación de asignación o **null**.

## <a name="return-value"></a>Valor devuelto

Cada función devuelve un puntero al nombre generado o **null** si se produce un error. Se puede producir un error si se especifica un nombre de directorio no válido en la variable de entorno TMP y en el parámetro *dir* .

> [!NOTE]
> **gratis** no es necesario llamar a (o **free_dbg**) para los punteros asignados por **_tempnam_dbg** y **_wtempnam_dbg**.

## <a name="remarks"></a>Comentarios

Las funciones **_tempnam_dbg** y **_wtempnam_dbg** son idénticas **a _tempnam** y **_wtempnam** , salvo que, cuando se define **_ Debug** , estas funciones usan la versión de depuración de **malloc** y **_ malloc_dbg**, para Asigne memoria si se pasa **null** como primer parámetro. Para obtener más información, consulte [_malloc_dbg](malloc-dbg.md).

En la mayoría de los casos, no es necesario llamar a estas funciones explícitamente en la mayoría. En su lugar, puede definir la marca _ **crtdbg_map_alloc**. Cuando se define _ **crtdbg_map_alloc** , las llamadas a **_tempnam** y **_wtempnam** se reasignan a **_tempnam_dbg** y **_Wtempnam_dbg**, respectivamente, con el *blockType* establecido en **_NORMAL_BLOCK**. Por lo tanto, no es necesario llamar a estas funciones explícitamente a menos que desee marcar los bloques del montón como _ **client_block**. Para obtener más información, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).

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
