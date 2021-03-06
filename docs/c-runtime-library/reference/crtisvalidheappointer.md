---
title: _CrtIsValidHeapPointer
ms.date: 11/04/2016
api_name:
- _CrtIsValidHeapPointer
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
- CrtlsValidHeapPointer
- _CrtIsValidHeapPointer
helpviewer_keywords:
- _CrtIsValidHeapPointer function
- CrtIsValidHeapPointer function
ms.assetid: caf597ce-1b05-4764-9f37-0197a982bec5
ms.openlocfilehash: 9a8746eb2da90ac5515d92113b977011a4647fe6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942384"
---
# <a name="_crtisvalidheappointer"></a>_CrtIsValidHeapPointer

Comprueba si un puntero especificado se encuentra en un montón asignado por alguna biblioteca en tiempo de ejecución de C, pero no necesariamente por la biblioteca CRT del autor de llamada. En las versiones de CRT anteriores a Visual Studio 2010, comprueba que el puntero especificado se encuentre en el montón local (solo en la versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
int _CrtIsValidHeapPointer(
   const void *userData
);
```

### <a name="parameters"></a>Parámetros

*userData*<br/>
Puntero al principio de un bloque de memoria asignado.

## <a name="return-value"></a>Valor devuelto

**_CrtIsValidHeapPointer** devuelve true si el puntero especificado está en el montón compartido por todas las instancias de la biblioteca CRT. En las versiones de CRT anteriores a Visual Studio 2010, devuelve TRUE si el puntero especificado se encuentra en el montón local. De lo contrario, la función devuelve el FALSE.

## <a name="remarks"></a>Comentarios

No se recomienda usar esta función. A partir de la biblioteca CRT de Visual Studio 2010, todas las bibliotecas CRT comparten un montón del SO, el *montón del proceso*. La función **_CrtIsValidHeapPointer** notifica si el puntero se asignó en un montón de CRT, pero no si lo asignó la biblioteca de CRT del llamador. Por ejemplo, tenga en cuenta un bloque asignado mediante la versión de Visual Studio 2010 de la biblioteca CRT. Si la función **_CrtIsValidHeapPointer** exportada por la versión de Visual Studio 2012 de la biblioteca CRT prueba el puntero, devuelve true. Esta prueba ya no es útil. En versiones anteriores a Visual Studio 2010 de la biblioteca CRT, la función se usa para garantizar que una dirección de memoria concreta está en el montón local. El montón local hace referencia al montón creado y administrado por una instancia determinada de la biblioteca en tiempo de ejecución de C. Si una biblioteca de vínculos dinámicos (DLL) contiene un vínculo estático a la biblioteca en tiempo de ejecución, tiene su propia instancia del montón en tiempo de ejecución y, por consiguiente, su propio montón, independiente del montón local de la aplicación. Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a **_CrtIsValidHeapPointer** se quitan durante el preprocesamiento.

Dado que esta función devuelve TRUE o FALSE, se puede pasar a una de las macros [_ASSERT](assert-asserte-assert-expr-macros.md) para crear un mecanismo sencillo de control de errores de depuración. En el ejemplo siguiente se genera un error de aserción si la dirección especificada no se está en el montón local:

```C
_ASSERTE( _CrtIsValidHeapPointer( userData ) );
```

Para obtener más información sobre cómo se puede usar **_CrtIsValidHeapPointer** con otras funciones de depuración y macros, vea [macros para informes](/visualstudio/debugger/macros-for-reporting). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtIsValidHeapPointer**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo probar si la memoria es válida cuando se utiliza con las bibliotecas de tiempo de ejecución de C anteriores a Visual Studio 2010. Este ejemplo se proporciona para los usuarios de código heredado de la biblioteca CRT.

```C
// crt_isvalid.c
// This program allocates a block of memory using _malloc_dbg
// and then tests the validity of this memory by calling
// _CrtIsMemoryBlock,_CrtIsValidPointer, and _CrtIsValidHeapPointer.

#include <stdio.h>
#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

#define  TRUE   1
#define  FALSE  0

int main( void )
{
    char *my_pointer;

    // Call _malloc_dbg to include the filename and line number
    // of our allocation request in the header information
    my_pointer = (char *)_malloc_dbg( sizeof(char) * 10,
        _NORMAL_BLOCK, __FILE__, __LINE__ );

    // Ensure that the memory got allocated correctly
    _CrtIsMemoryBlock((const void *)my_pointer, sizeof(char) * 10,
        NULL, NULL, NULL );

    // Test for read/write accessibility
    if (_CrtIsValidPointer((const void *)my_pointer,
        sizeof(char) * 10, TRUE))
        printf("my_pointer has read and write accessibility.\n");
    else
        printf("my_pointer only has read access.\n");

    // Make sure my_pointer is within the local heap
    if (_CrtIsValidHeapPointer((const void *)my_pointer))
        printf("my_pointer is within the local heap.\n");
    else
        printf("my_pointer is not located within the local"
               " heap.\n");

    free(my_pointer);
}
```

```Output
my_pointer has read and write accessibility.
my_pointer is within the local heap.
```

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
