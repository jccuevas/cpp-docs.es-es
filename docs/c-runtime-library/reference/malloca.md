---
title: _malloca
ms.date: 11/04/2016
api_name:
- _malloca
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
- malloca
- _malloca
helpviewer_keywords:
- memory allocation, stack
- malloca function
- _malloca function
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
ms.openlocfilehash: 0b12b4adde710f2fc46b3a3790519006fabbb1fc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952777"
---
# <a name="_malloca"></a>_malloca

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

La rutina **_malloca** devuelve un puntero **void** al espacio asignado, cuya alineación es adecuada para el almacenamiento de cualquier tipo de objeto. Si *el tamaño* es 0, **_malloca** asigna un elemento de longitud cero y devuelve un puntero válido a ese elemento.

Si el *tamaño* es mayor que **_ALLOCA_S_THRESHOLD**, **_malloca** intenta asignar en el montón y devuelve un puntero nulo si no se puede asignar el espacio. Si el *tamaño* es menor o igual que **_ALLOCA_S_THRESHOLD**, **_malloca** intenta asignar en la pila y se genera una excepción de desbordamiento de pila si no se puede asignar el espacio. La excepción de desbordamiento de pila C++ no es una excepción; se trata de una excepción estructurada. En lugar de usar C++ el control de excepciones, debe usar el [control de excepciones estructurado](../../cpp/structured-exception-handling-c-cpp.md) (SEH) para detectar esta excepción.

## <a name="remarks"></a>Comentarios

**_malloca** asigna bytes de *tamaño* de la pila del programa o del montón si la solicitud supera un determinado tamaño en bytes dado por **_ALLOCA_S_THRESHOLD**. La diferencia entre **_malloca** y _ **alloca** es que _ **alloca** siempre asigna en la pila, independientemente del tamaño. A diferencia de _ **alloca**, que no requiere ni permite una **llamada a Free** para liberar la memoria de modo que se asigne, **_malloca** requiere el uso de [_freea](freea.md) para liberar memoria. En el modo de depuración, **_malloca** siempre asigna memoria del montón.

Existen restricciones para llamar explícitamente a **_malloca** en un controlador de excepciones (EH). Las rutinas EH que se ejecutan en procesadores de clase x86 funcionan en su propio marco de memoria: Realizan sus tareas en el espacio de memoria que no se basa en la ubicación actual del puntero de pila de la función de inclusión. Las implementaciones más habituales incluyen el control de excepciones estructuradas (SEH) de Windows NT y las expresiones de la cláusula catch de C++. Por consiguiente, si se llama explícitamente a **_malloca** en cualquiera de los siguientes escenarios, se produce un error en el programa durante la devolución a la rutina de llamada EH:

- Expresión de filtro de excepciones SEH de Windows NT`_malloca ()` : **_ _ Except** ()

- Controlador de excepciones final de SEH de Windows NT`_malloca ()` : **_ _ Finally** {}

- Expresión de la cláusula catch del controlador de excepciones de C++

Sin embargo, se puede llamar a **_malloca** directamente desde una rutina EH o desde una devolución de llamada proporcionada por la aplicación que se invoca mediante uno de los escenarios EH descritos anteriormente.

> [!IMPORTANT]
> En Windows XP, si se llama a **_malloca** dentro de un bloque try/catch, debe llamar a [_resetstkoflw](resetstkoflw.md) en el bloque catch.

Además de las restricciones anteriores, al usar la opción [/CLR (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) , **_malloca** no se puede usar en bloques **_ _ Except** . Para obtener más información, consulta [/clr Restrictions](../../build/reference/clr-restrictions.md).

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
