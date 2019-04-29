---
title: _CrtIsMemoryBlock
ms.date: 11/04/2016
apiname:
- _CrtIsMemoryBlock
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
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
ms.openlocfilehash: c4a85ebeb45552c6f5355853de2a45766d6bc984
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339902"
---
# <a name="crtismemoryblock"></a>_CrtIsMemoryBlock

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
Puntero al número de asignación del bloque o **NULL**.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó el bloque o **NULL**.

*linenumber*<br/>
Puntero al número de línea en el archivo de origen o **NULL**.

## <a name="return-value"></a>Valor devuelto

**_CrtIsMemoryBlock** devuelve **TRUE** si el bloque de memoria especificado está ubicado en el montón local y tiene un identificador de tipo de bloque del montón de depuración válido; en caso contrario, la función devuelve **FALSE**.

## <a name="remarks"></a>Comentarios

El **_CrtIsMemoryBlock** función simplemente comprueba que un bloque de memoria especificado está ubicado en el montón local de la aplicación y que tiene un identificador de tipo de bloque válido. Esta función también se puede usar para obtener el número de orden de la asignación de objetos, y el nombre y el número de línea del archivo de código fuente en el que se solicitó la asignación del bloque de memoria originalmente. Pasar que no sean de**NULL** valores para el *requestNumber*, *filename*, o *linenumber* causas de los parámetros **_ CrtIsMemoryBlock** para establecer estos parámetros a los valores de encabezado de depuración del bloque de memoria, si encuentra el bloque en el montón local. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, las llamadas a **_CrtIsMemoryBlock** se quitan durante el preprocesamiento.

Si **_CrtIsMemoryBlock** produce un error, devuelve **FALSE** y los parámetros de salida se inicializan en los valores predeterminados: *requestNumber* y **lineNumber**  se establecen en 0 y *filename* está establecido en **NULL**.

Dado que esta función devuelve **TRUE** o **FALSE**, se puede pasar a una de las macros [_ASSERT](assert-asserte-assert-expr-macros.md) para crear un mecanismo sencillo de control de errores de depuración. En el ejemplo siguiente se genera un error de aserción si la dirección especificada no se está en el montón local:

```C
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,
          &filename, &linenumber ) );
```

Para obtener más información acerca de cómo **_CrtIsMemoryBlock** puede utilizarse con otras macros y funciones de depuración, vea [Macros para los informes](/visualstudio/debugger/macros-for-reporting). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

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
