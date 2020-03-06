---
title: MatchEventStack
description: La C++ referencia de la función MATCHEVENTSTACK del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 445c2d00c24da10754d32256de0c691e82b557e1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334365"
---
# <a name="matcheventstack"></a>MatchEventStack

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `MatchEventStack` se usa para hacer coincidir una pila de eventos con una jerarquía de eventos específica. Las jerarquías coincidentes se reenvían a un controlador para su posterior procesamiento. Para obtener más información sobre eventos, pilas de eventos y jerarquías, vea [tabla de eventos](../event-table.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename          TEvent,
    typename...       TEvents,
    typename          TCallable,
    typename...       TExtraArgs>
bool MatchEventStack(
    const EventStack& eventStack,
    TCallable&&       callable,
    TExtraArgs&&...   extraArgs);
```

### <a name="parameters"></a>Parámetros

\ *TEvent*
Tipo del elemento primario de Eldest que debe coincidir en la pila de eventos.

\ *TEvents*
Los tipos restantes que desea buscar en la pila de eventos.

\ *TCallable*
Tipo que admite `operator()`. Para obtener más información sobre qué argumentos se pasan a este operador, vea la descripción del parámetro al que se *puede llamar* .

\ *TExtraArgs*
Tipos de los argumentos adicionales pasados a `MatchEventStack`.

\ *eventStack*
Pila de eventos que debe coincidir con la jerarquía de tipos de evento descrita por *TEvent* y *TEvents*.

\ *invocable*
Tras hacer coincidir correctamente la pila de eventos con la jerarquía de tipos de evento descrita por *TEvent* y *TEvents*, `MatchEventStack` invoca a *Callable*. Pasa a un argumento de valor *r para cada* tipo en la jerarquía de eventos. El paquete de parámetros de *extraargs* se reenvía de forma perfecta en el resto de los parámetros de a los que se *puede llamar*.

\ *Extraargs*
Los argumentos que se reenvían de la ruta a la que se *puede llamar* junto con el tipo de evento coincidente.

### <a name="return-value"></a>Valor devuelto

Valor **booleano** que es **true** si la coincidencia se realizó correctamente, o **false** en caso contrario.

## <a name="remarks"></a>Comentarios

El último evento de *eventStack* siempre coincide con la última entrada de la lista de tipos concatenados de la \[*TEvent*, *TEvents...* \]. Todas las demás entradas de *TEvent* y *TEvents* pueden coincidir con cualquier posición en *eventStack* excepto en la última, siempre que estén en el mismo orden.

Los tipos de evento que se van a usar para los parámetros *TEvent* y *TEvents* se seleccionan de una lista de *clases de captura*. Para obtener una lista de eventos y las clases de captura que puede usar para hacerlos coincidir, consulte [tabla de eventos](../event-table.md).

## <a name="example"></a>Ejemplo

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStack<Compiler, BackEndPass, C2DLL,
                CodeGeneration, Thread, Function>(
        eventStack, [](Compiler cl, BackEndPass bep, C2DLL c2,
            CodeGeneration cg, Thread t, Function f){ /* Do something ... */ });

    bool b2 = MatchEventStack<Compiler, Function>(
        eventStack, [](Compiler cl, Function f){ /* Do something... */ });

    bool b3 = MatchEventStack<Thread, Compiler, Function>(
        eventStack, [](Thread t, Compiler cl Function f){ /* Do something... */ });

    bool b4 = MatchEventStack<Compiler>(
        eventStack, [](Compiler cl){ /* Do something... */ });


    // b1: true because the list of types matches the eventStack exactly.
    // b2: true because Function is the last entry in both the type list
    //     and 'eventStack', and also because Compiler comes before
    //     Function in 'eventStack' and in the type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', they aren't listed in the
    //     right order in the type list.
    // b4: false because the last entry in the type list is Compiler,
    //     which doesn't match the last entry in 'eventStack' (Function).
}
```

::: moniker-end
