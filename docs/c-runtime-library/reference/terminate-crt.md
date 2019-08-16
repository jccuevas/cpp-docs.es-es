---
title: terminate (CRT)
ms.date: 11/04/2016
apiname:
- terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- terminate
helpviewer_keywords:
- terminate function
- exception handling, termination
ms.assetid: 90e67402-08e9-4b2a-962c-66a8afd3ccb4
ms.openlocfilehash: 1f655d328b4d97a2989ad49005ed8a9f44fd9d79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155633"
---
# <a name="terminate-crt"></a>terminate (CRT)

Las llamadas [anular](abort.md) o una función que especifique mediante **set_terminate**.

## <a name="syntax"></a>Sintaxis

```C
void terminate( void );
```

## <a name="remarks"></a>Comentarios

El **finalizar** función se usa con control de excepciones de C++ y se llama en los casos siguientes:

- Cuando no se encuentra un controlador catch coincidente para una excepción de C++.

- Cuando una función de destructor produce una excepción durante un desenredo de pila.

- Cuando la pila se daña después de producir una excepción.

**Finalizar** llamadas [anular](abort.md) de forma predeterminada. Puede cambiar este comportamiento predeterminado escribiendo su propia función de finalización y llamar a **set_terminate** con el nombre de la función como su argumento. **Finalizar** llama a la última función especificada como argumento a **set_terminate**. Para más información, vea [Excepciones de C++ no controladas](../../cpp/unhandled-cpp-exceptions.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**terminate**|\<eh.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```cpp
// crt_terminate.cpp
// compile with: /EHsc
#include <eh.h>
#include <process.h>
#include <iostream>
using namespace std;

void term_func();

int main()
{
    int i = 10, j = 0, result;
    set_terminate( term_func );
    try
    {
        if( j == 0 )
            throw "Divide by zero!";
        else
            result = i/j;
    }
    catch( int )
    {
        cout << "Caught some integer exception.\n";
    }
    cout << "This should never print.\n";
}

void term_func()
{
    cout << "term_func() was called by terminate().\n";

    // ... cleanup tasks performed here

    // If this function does not exit, abort is called.

    exit(-1);
}
```

```Output
term_func() was called by terminate().
```

## <a name="see-also"></a>Vea también

[Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
