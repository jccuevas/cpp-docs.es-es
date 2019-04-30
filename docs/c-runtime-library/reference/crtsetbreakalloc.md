---
title: _CrtSetBreakAlloc
ms.date: 11/04/2016
apiname:
- _CrtSetBreakAlloc
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
- CrtSetBreakAlloc
- _CrtSetBreakAlloc
helpviewer_keywords:
- CrtSetBreakAlloc function
- _CrtSetBreakAlloc function
ms.assetid: 33bfc6af-a9ea-405b-a29f-1c2d4d9880a1
ms.openlocfilehash: bbc4b0de553533dde95f37675b3c9234569e3505
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342951"
---
# <a name="crtsetbreakalloc"></a>_CrtSetBreakAlloc

Establece un punto de interrupción en un número de orden de asignación de objetos especificado (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
long _CrtSetBreakAlloc(
   long lBreakAlloc
);
```

### <a name="parameters"></a>Parámetros

*lBreakAlloc*<br/>
Número de orden de asignación para el que se va a establecer el punto de interrupción.

## <a name="return-value"></a>Valor devuelto

Devuelve el número de orden de asignación de objetos anterior que tenía establecido un punto de interrupción.

## <a name="remarks"></a>Comentarios

**_CrtSetBreakAlloc** permite que una aplicación realizar la detección de pérdidas de memoria mediante la separación en un momento concreto de asignación de memoria y la trazabilidad del origen de la solicitud. La función usa el número de orden de la asignación de objetos secuencial asignado al bloque de memoria cuando se asignó en el montón. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, las llamadas a **_CrtSetBreakAlloc** se quitan durante el preprocesamiento.

El número de orden de la asignación de objetos se almacena en el campo *lRequest* de la estructura **_CrtMemBlockHeader**, que se define en Crtdbg.h. Cuando se proporciona información sobre un bloque de memoria por una de las funciones de volcado de depuración, este número aparece encerrado entre llaves, como {36}.

Para obtener más información acerca de cómo **_CrtSetBreakAlloc** puede utilizarse con otras funciones de administración de memoria, vea [seguimiento de solicitudes de asignación del montón](/visualstudio/debugger/crt-debug-heap-details). Para más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtSetBreakAlloc**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_setbrkal.c
// compile with: -D_DEBUG /MTd -Od -Zi -W3 /c /link -verbose:lib -debug

/*
* In this program, a call is made to the _CrtSetBreakAlloc routine
* to verify that the debugger halts program execution when it reaches
* a specified allocation number.
*/

#include <malloc.h>
#include <crtdbg.h>

int main( )
{
        long allocReqNum;
        char *my_pointer;

        /*
         * Allocate "my_pointer" for the first
         * time and ensure that it gets allocated correctly
         */
        my_pointer = malloc(10);
        _CrtIsMemoryBlock(my_pointer, 10, &allocReqNum, NULL, NULL);

        /*
         * Set a breakpoint on the allocation request
         * number for "my_pointer"
         */
        _CrtSetBreakAlloc(allocReqNum+2);

        /*
         * Alternate freeing and reallocating "my_pointer"
         * to verify that the debugger halts program execution
         * when it reaches the allocation request
         */
        free(my_pointer);
        my_pointer = malloc(10);
        free(my_pointer);
        my_pointer = malloc(10);
        free(my_pointer);
}
```

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
