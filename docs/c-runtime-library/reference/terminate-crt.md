---
title: terminate (CRT)
ms.date: 4/2/2020
api_name:
- terminate
- _o_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- terminate
helpviewer_keywords:
- terminate function
- exception handling, termination
ms.assetid: 90e67402-08e9-4b2a-962c-66a8afd3ccb4
ms.openlocfilehash: 1ec4e27096dd6b5fea089e21c95022542d7adc82
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912225"
---
# <a name="terminate-crt"></a>terminate (CRT)

Llama a [Abort](abort.md) o a una función que especifique mediante **set_terminate**.

## <a name="syntax"></a>Sintaxis

```C
void terminate( void );
```

## <a name="remarks"></a>Observaciones

La función **Terminate** se usa con el control de excepciones de C++ y se llama en los casos siguientes:

- Cuando no se encuentra un controlador catch coincidente para una excepción de C++.

- Cuando una función de destructor produce una excepción durante un desenredo de pila.

- Cuando la pila se daña después de producir una excepción.

la instrucción **Terminate** llama a [Abort](abort.md) de forma predeterminada. Puede cambiar este valor predeterminado si escribe su propia función de finalización y llama a **set_terminate** con el nombre de la función como su argumento. **Terminate** llama a la última función especificada como argumento para **set_terminate**. Para más información, vea [Excepciones de C++ no controladas](../../cpp/unhandled-cpp-exceptions.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**cancela**|\<eh.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)<br/>
[aborta](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[esperado](unexpected-crt.md)<br/>
