---
title: MatchEvent
description: Referencia de la función MatchEvent del SDK de C+++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0c60653641c676716bcdd60865433773da79325f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323855"
---
# <a name="matchevent"></a>MatchEvent

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `MatchEvent` función se utiliza para hacer coincidir un evento con una lista de tipos de eventos. Si el evento coincide con un tipo de la lista, se reenvía a un controlador para su posterior procesamiento.

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename        TEvent,
    typename...     TEvents,
    typename        TCallable,
    typename...     TExtraArgs>
bool MatchEvent(
    const RawEvent& event,
    TCallable&&     callable,
    TExtraArgs&&... extraArgs);
```

### <a name="parameters"></a>Parámetros

*TEvent*\
El primer tipo de evento que desea que coincida.

*TEvents*\
Los tipos de eventos restantes que desea que coincidan.

*TCallable*\
Un tipo `operator()`que admite . Para obtener más información sobre qué argumentos se pasan a este operador, vea la descripción del parámetro *invocable.*

*TExtraArgs*\
Los tipos de los argumentos `MatchEvent`adicionales que se pasaron a .

*Evento*\
Evento que se va a hacer coincidir con los tipos de eventos descritos por *TEvent* y *TEvents*.

*Accesible*\
`MatchEvent`invoca *a los que se puede llamar* después de hacer coincidir correctamente el evento con cualquiera de los tipos de eventos descritos por *TEvent* y *TEvents*. El primer argumento pasado a *callable* es un valor r del tipo de evento coincidente. El paquete de parámetros *extraArgs* se reenvía perfectamente en los parámetros restantes de *callable*.  

*extraArgs*\
Los argumentos que se reenvían perfectamente a *invocables* junto con el tipo de evento coincidente.

### <a name="return-value"></a>Valor devuelto

Un valor **bool** que es **true** si la coincidencia se realizó correctamente, o **false** en caso contrario.

## <a name="remarks"></a>Observaciones

Los tipos de eventos que se van a utilizar para los parámetros *TEvent* y *TEvents* se seleccionan de una lista de clases de *captura.* Para obtener una lista de eventos y las clases de captura que puede usar para hacer coincidirlos, consulte [la tabla](../event-table.md)de eventos .

## <a name="example"></a>Ejemplo

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEvent<Function, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});

    bool b2 = MatchEvent<CodeGeneration, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});


    // b1: true because the list of types contains Function, which is
    //     the type of the event we are trying to match.
    // b2: false because the list of types doesn't contain Function.
}
```

::: moniker-end
