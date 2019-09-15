---
title: _alloca
ms.date: 11/04/2016
api_name:
- _alloca
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
- _alloca
- alloca
helpviewer_keywords:
- memory allocation, stack
- alloca function
- _alloca function
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
ms.openlocfilehash: 2212f9e40c78932b63eebfc221ad2f07fa3d3f9d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943697"
---
# <a name="_alloca"></a>_alloca

Asigna memoria en la pila. Esta función está en desuso porque hay disponible una versión más segura; vea [_malloca](malloca.md).

## <a name="syntax"></a>Sintaxis

```C
void *_alloca(
   size_t size
);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Bytes que se van a asignar desde la pila.

## <a name="return-value"></a>Valor devuelto

La rutina _ **alloca** devuelve un puntero **void** al espacio asignado, cuya alineación está garantizada para el almacenamiento de cualquier tipo de objeto. Si *el tamaño* es 0, _ **alloca** asigna un elemento de longitud cero y devuelve un puntero válido a ese elemento.

Si no se puede asignar el espacio, se genera una excepción de desbordamiento de pila. La excepción de desbordamiento de pila no es una excepción de C++, sino que es una excepción estructurada. En lugar de usar el control de excepciones de C++, debe usar el [control de excepciones estructuradas](../../cpp/structured-exception-handling-c-cpp.md) (SEH).

## <a name="remarks"></a>Comentarios

_ **alloca** asigna bytes de *tamaño* de la pila del programa. El espacio asignado se libera automáticamente cuando finaliza la función de llamada (no cuando la asignación pasa simplemente fuera del ámbito). Por lo tanto, no pase el valor de puntero devuelto por _ **alloca** como argumento a [Free](free.md).

Hay restricciones para llamar explícitamente a _ **alloca** en un controlador de excepciones (EH). Las rutinas EH que se ejecutan en procesadores de clase x86 funcionan en su propio marco de memoria: Realizan sus tareas en el espacio de memoria que no se basa en la ubicación actual del puntero de pila de la función de inclusión. Las implementaciones más habituales incluyen el control de excepciones estructuradas (SEH) de Windows NT y las expresiones de la cláusula catch de C++. Por consiguiente, si se llama explícitamente a _ **alloca** en cualquiera de los siguientes escenarios, se produce un error en el programa durante la devolución a la rutina de llamada EH:

- Expresión de filtro de excepciones SEH de Windows NT:`__except ( _alloca() )`

- Controlador de excepciones final de SEH de Windows NT:`__finally { _alloca() }`

- Expresión de la cláusula catch del controlador de excepciones de C++

Sin embargo, se puede llamar a _ **alloca** directamente desde una rutina EH o desde una devolución de llamada proporcionada por la aplicación que se invoca mediante uno de los escenarios EH enumerados anteriormente.

> [!IMPORTANT]
> En Windows XP, si se llama a _ **alloca** dentro de un bloque try/catch, debe llamar a [_resetstkoflw](resetstkoflw.md) en el bloque catch.

Además de las restricciones anteriores, cuando se usa la opción[/CLR (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) , _ **allocate** no se puede usar en bloques **_ _ Except** . Para obtener más información, consulta [/clr Restrictions](../../build/reference/clr-restrictions.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_alloca**|\<malloc.h>|

## <a name="example"></a>Ejemplo

```C
// crt_alloca.c
// This program demonstrates the use of
// _alloca and trapping any exceptions
// that may occur.

#include <windows.h>
#include <stdio.h>
#include <malloc.h>

int main()
{
    int     size = 1000;
    int     errcode = 0;
    void    *pData = NULL;

    // Note: Do not use try/catch for _alloca,
    // use __try/__except, since _alloca throws
    // Structured Exceptions, not C++ exceptions.

    __try {
        // An unbounded _alloca can easily result in a
        // stack overflow.
        // Checking for a size < 1024 bytes is recommended.
        if (size > 0 && size < 1024)
        {
            pData = _alloca( size );
            printf_s( "Allocated %d bytes of stack at 0x%p",
                      size, pData);
        }
        else
        {
            printf_s("Tried to allocate too many bytes.\n");
        }
    }

    // If an exception occured with the _alloca function
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )
    {
        printf_s("_alloca failed!\n");

        // If the stack overflows, use this function to restore.
        errcode = _resetstkoflw();
        if (errcode)
        {
            printf_s("Could not reset the stack!\n");
            _exit(1);
        }
    };
}
```

```Output
Allocated 1000 bytes of stack at 0x0012FB50
```

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_resetstkoflw](resetstkoflw.md)<br/>
[_malloca](malloca.md)<br/>
