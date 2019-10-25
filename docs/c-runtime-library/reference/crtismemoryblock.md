---
title: _CrtIsMemoryBlock
ms.date: 11/04/2016
api_name:
- _CrtIsMemoryBlock
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
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
ms.openlocfilehash: f29745acd06f6f5b3fa96367444e800bdc3e8e3a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938732"
---
# <a name="_crtismemoryblock"></a>_CrtIsMemoryBlock

Comprueba que un bloque de memoria especificado está en el montón local y que tiene un identificador válido de tipo de bloque del montón de depuración (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
int _CrtIsMemoryBlock(
   const void *userData,
   unsigned int size,
   long *requestNumber,
   char **filename,
   int *linenumber
);
```

### <a name="parameters"></a>Parámetros

*userData*<br/>
Puntero al principio del bloque de memoria que se va a comprobar.

*size*<br/>
Tamaño del bloque especificado, en bytes.

*requestNumber*<br/>
Puntero al número de asignación del bloque o **null**.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó el bloque o **null**.

*linenumber*<br/>
Puntero al número de línea del archivo de código fuente o **null**.

## <a name="return-value"></a>Valor devuelto

**_CrtIsMemoryBlock** devuelve **true** si el bloque de memoria especificado se encuentra en el montón local y tiene un identificador de tipo de bloque de montón de depuración válido. de lo contrario, la función devuelve **false**.

## <a name="remarks"></a>Comentarios

La función **_CrtIsMemoryBlock** comprueba que un bloque de memoria especificado se encuentra en el montón local de la aplicación y que tiene un identificador de tipo de bloque válido. Esta función también se puede usar para obtener el número de orden de la asignación de objetos, y el nombre y el número de línea del archivo de código fuente en el que se solicitó la asignación del bloque de memoria originalmente. Pasar valores no**null** para los parámetros *requestNumber*, *filename*o *lineNumber* hace que **_CrtIsMemoryBlock** establezca estos parámetros en los valores del encabezado de depuración del bloque de memoria, si encuentra el bloque en el montón local. Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a **_CrtIsMemoryBlock** se quitan durante el preprocesamiento.

Si **_CrtIsMemoryBlock** produce un error, devuelve **false** y los parámetros de salida se inicializan en los valores predeterminados: *requestNumber* y **lineNumber** se establecen en 0 y *filename* se establece en **null**.

Dado que esta función devuelve **TRUE** o **FALSE**, se puede pasar a una de las macros [_ASSERT](assert-asserte-assert-expr-macros.md) para crear un mecanismo sencillo de control de errores de depuración. En el ejemplo siguiente se genera un error de aserción si la dirección especificada no se está en el montón local:

```C
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,
          &filename, &linenumber ) );
```

Para obtener más información sobre cómo se puede usar **_CrtIsMemoryBlock** con otras funciones de depuración y macros, vea [macros para informes](/visualstudio/debugger/macros-for-reporting). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtIsMemoryBlock**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo del tema [_CrtIsValidHeapPointer](crtisvalidheappointer.md).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
