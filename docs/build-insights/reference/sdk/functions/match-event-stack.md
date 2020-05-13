---
title: MatchEventStack
description: Referencia de la función MatchEventStack del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a223d420e8c48667fbd1c6569f02d0486f597b5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323871"
---
# <a name="matcheventstack"></a>MatchEventStack

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `MatchEventStack` función se utiliza para hacer coincidir una pila de eventos con una jerarquía de eventos específica. Las jerarquías coincidentes se reenvían a un controlador para su posterior procesamiento. Para obtener más información sobre eventos, pilas de eventos y jerarquías, consulte Tabla de [eventos](../event-table.md).

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

*TEvent*\
El tipo del elemento primario mayor que coincide en la pila de eventos.

*TEvents*\
Los tipos restantes que desea que coincidan en la pila de eventos.

*TCallable*\
Un tipo `operator()`que admite . Para obtener más información sobre qué argumentos se pasan a este operador, vea la descripción del parámetro *invocable.*

*TExtraArgs*\
Los tipos de los argumentos adicionales pasados a `MatchEventStack`.

*eventStack*\
La pila de eventos que debe coincidir con la jerarquía de tipos de evento descrita por *TEvent* y *TEvents*.

*Accesible*\
Al hacer coincidir correctamente la pila de eventos con la `MatchEventStack` jerarquía de tipos de eventos descrita por *TEvent* y *TEvents*, invoca *el valor invocable*. Pasa a un argumento de valor r *invocable* para cada tipo en la jerarquía de eventos. El paquete de parámetros *extraArgs* se reenvía perfectamente en los parámetros restantes de *callable*.

*extraArgs*\
Los argumentos que se reenvían perfectamente a *invocables* junto con el tipo de evento coincidente.

### <a name="return-value"></a>Valor devuelto

Un valor **bool** que es **true** si la coincidencia se realizó correctamente, o **false** en caso contrario.

## <a name="remarks"></a>Observaciones

El último evento de *eventStack* siempre coincide con la \[última entrada del *TEvent*concatenado, *TEvents...* \] tipo lista. Todas las demás entradas *de TEvent* y *TEvents* pueden coincidir con cualquier posición en *eventStack* excepto la última, siempre que estén en el mismo orden.

Los tipos de eventos que se van a utilizar para los parámetros *TEvent* y *TEvents* se seleccionan de una lista de clases de *captura.* Para obtener una lista de eventos y las clases de captura que puede usar para hacer coincidirlos, consulte [la tabla](../event-table.md)de eventos .

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
