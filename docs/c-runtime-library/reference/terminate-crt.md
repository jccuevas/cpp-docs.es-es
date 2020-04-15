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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 1aa95daeab424c933f10060fb4f87cb317aa188c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362542"
---
# <a name="terminate-crt"></a>terminate (CRT)

Las llamadas [abortan](abort.md) o una función que especifique mediante **set_terminate**.

## <a name="syntax"></a>Sintaxis

```C
void terminate( void );
```

## <a name="remarks"></a>Observaciones

La función **terminate** se utiliza con el control de excepciones C++ y se llama en los siguientes casos:

- Cuando no se encuentra un controlador catch coincidente para una excepción de C++.

- Cuando una función de destructor produce una excepción durante un desenredo de pila.

- Cuando la pila se daña después de producir una excepción.

**terminar** las llamadas [abortan de](abort.md) forma predeterminada. Puede cambiar este valor predeterminado escribiendo su propia función de terminación y llamando a **set_terminate** con el nombre de la función como argumento. **terminate** llama a la última función dada como argumento para **set_terminate**. Para más información, vea [Excepciones de C++ no controladas](../../cpp/unhandled-cpp-exceptions.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**Terminar**|\<eh.h>|

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
[Aborta](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Inesperado](unexpected-crt.md)<br/>
