---
title: _malloca
ms.date: 11/04/2016
apiname:
- _malloca
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
- malloca
- _malloca
helpviewer_keywords:
- memory allocation, stack
- malloca function
- _malloca function
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
ms.openlocfilehash: 8c8ce8bdf8ab40cae45ecec9c4b182bdf3d6bc82
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563987"
---
# <a name="malloca"></a>_malloca

Asigna memoria en la pila. Se trata de una versión de [_alloca](alloca.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
void *_malloca(
   size_t size
);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Bytes que se van a asignar desde la pila.

## <a name="return-value"></a>Valor devuelto

El **_malloca** rutinarias devuelve un **void** puntero en el espacio asignado, que se garantiza que se alinee correctamente para el almacenamiento de cualquier tipo de objeto. Si *tamaño* es 0, **_malloca** asigna un elemento de longitud cero y devuelve un puntero válido para ese elemento.

Si no se puede asignar el espacio, se genera una excepción de desbordamiento de pila. La excepción de desbordamiento de pila no es una excepción de C++, sino que es una excepción estructurada. En lugar de usar el control de excepciones de C++, debe usar el [control de excepciones estructuradas](../../cpp/structured-exception-handling-c-cpp.md) (SEH).

## <a name="remarks"></a>Comentarios

**_malloca** asigna *tamaño* bytes a partir de la pila del programa o el montón si la solicitud supera un determinado tamaño en bytes proporcionado por **_ALLOCA_S_THRESHOLD**. La diferencia entre **_malloca** y **_alloca** es que **_alloca** siempre se asigna en la pila, independientemente del tamaño. A diferencia de **_alloca**, que no requiere ni permite ninguna llamada a **libre** para liberar la memoria asignada, **_malloca** requiere el uso de [_freea](freea.md)para liberar memoria. En modo de depuración, **_malloca** siempre asigna memoria del montón.

Hay restricciones para llamar explícitamente a **_malloca** en un controlador de excepciones (EH). Las rutinas del controlador de excepciones que se ejecutan en procesadores de clase x86 funcionan en su propio marco de memoria: llevan a cabo sus tareas en el espacio de memoria que no se basa en la ubicación actual del puntero de pila de la función de inclusión. Las implementaciones más habituales incluyen el control de excepciones estructuradas (SEH) de Windows NT y las expresiones de la cláusula catch de C++. Por lo tanto, llamar explícitamente a **_malloca** en cualquiera de lo siguientes escenarios, se produce un error del programa durante la devolución de la rutina de controlador de eventos que realiza la llamada:

- Expresión de filtro de excepciones SEH de Windows NT: **__except** (`_malloca ()` )

- Controlador de excepciones finales SEH de Windows NT: **__finally** {`_malloca ()` }

- Expresión de la cláusula catch del controlador de excepciones de C++

Sin embargo, **_malloca** pueden llamarse directamente desde dentro de una rutina de controlador de excepciones o desde una devolución de llamada proporcionada por la aplicación que se invoca mediante uno de los escenarios EH enumerados anteriormente.

> [!IMPORTANT]
> En Windows XP, si **_malloca** se llama dentro de un bloque try/catch, se debe llamar a [_resetstkoflw](resetstkoflw.md) en el bloque catch.

Además de las restricciones anteriores, cuando se usa el [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) opción, **_malloca** no se puede usar en **__except** bloques. Para obtener más información, consulta [/clr Restrictions](../../build/reference/clr-restrictions.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_malloca**|\<malloc.h>|

## <a name="example"></a>Ejemplo

```C
// crt_malloca_simple.c
#include <stdio.h>
#include <malloc.h>

void Fn()
{
   char * buf = (char *)_malloca( 100 );
   // do something with buf
   _freea( buf );
}

int main()
{
   Fn();
}
```

## <a name="example"></a>Ejemplo

```C
// crt_malloca_exception.c
// This program demonstrates the use of
// _malloca and trapping any exceptions
// that may occur.

#include <windows.h>
#include <stdio.h>
#include <malloc.h>

int main()
{
    int     size;
    int     numberRead = 0;
    int     errcode = 0;
    void    *p = NULL;
    void    *pMarker = NULL;

    while (numberRead == 0)
    {
        printf_s("Enter the number of bytes to allocate "
                 "using _malloca: ");
        numberRead = scanf_s("%d", &size);
    }

    // Do not use try/catch for _malloca,
    // use __try/__except, since _malloca throws
    // Structured Exceptions, not C++ exceptions.

    __try
    {
        if (size > 0)
        {
            p =  _malloca( size );
        }
        else
        {
            printf_s("Size must be a positive number.");
        }
        _freea( p );
    }

    // Catch any exceptions that may occur.
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )
    {
        printf_s("_malloca failed!\n");

        // If the stack overflows, use this function to restore.
        errcode = _resetstkoflw();
        if (errcode)
        {
            printf("Could not reset the stack!");
            _exit(1);
        }
    };
}
```

### <a name="input"></a>Entrada

```Input
1000
```

### <a name="sample-output"></a>Resultados del ejemplo

```Output
Enter the number of bytes to allocate using _malloca: 1000
```

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_resetstkoflw](resetstkoflw.md)<br/>
