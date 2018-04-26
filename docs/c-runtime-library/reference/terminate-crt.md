---
title: terminate (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- terminate function
- exception handling, termination
ms.assetid: 90e67402-08e9-4b2a-962c-66a8afd3ccb4
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 302bb0096bd6b4d0b9e92c3508704f35f2c355c8
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="terminate-crt"></a>terminate (CRT)

Llamadas [anular](abort.md) o una función especifique mediante **set_terminate**.

## <a name="syntax"></a>Sintaxis

```C
void terminate( void );
```

## <a name="remarks"></a>Comentarios

El **finalizar** función se usa con control de excepciones de C++ y se llama en los casos siguientes:

- Cuando no se encuentra un controlador catch coincidente para una excepción de C++.

- Cuando una función de destructor produce una excepción durante un desenredo de pila.

- Cuando la pila se daña después de producir una excepción.

**terminar** llamadas [anular](abort.md) de forma predeterminada. Puede cambiar este comportamiento predeterminado escribiendo su propia función de finalización y llamando a **set_terminate** con el nombre de la función como su argumento. **terminar** llama a la última función especificada como argumento a **set_terminate**. Para más información, vea [Excepciones de C++ no controladas](../../cpp/unhandled-cpp-exceptions.md).

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
