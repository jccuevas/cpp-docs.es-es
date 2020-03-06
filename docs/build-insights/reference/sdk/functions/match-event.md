---
title: MatchEvent
description: La C++ referencia de la función MATCHEVENT del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f8022953e2f56f7c8917f161b094c50e0c5ecbdf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334359"
---
# <a name="matchevent"></a>MatchEvent

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `MatchEvent` se usa para hacer coincidir un evento con una lista de tipos de evento. Si el evento coincide con un tipo de la lista, se reenvía a un controlador para su posterior procesamiento.

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

\ *TEvent*
El primer tipo de evento que desea comparar.

\ *TEvents*
Los tipos de evento restantes que desea buscar.

\ *TCallable*
Tipo que admite `operator()`. Para obtener más información sobre qué argumentos se pasan a este operador, vea la descripción del parámetro al que se *puede llamar* .

\ *TExtraArgs*
Tipos de los argumentos adicionales que se pasaron a `MatchEvent`.

*event*\
Evento que debe coincidir con los tipos de evento descritos por *TEvent* y *TEvents*.

\ *invocable*
`MatchEvent` invoca a *Callable* después de que coincida correctamente el evento con cualquiera de los tipos de evento descritos por *TEvent* y *TEvents*. El primer argumento pasado a *Callable* es un valor r del tipo de evento coincidente. El paquete de parámetros de *extraargs* se reenvía de forma perfecta en el resto de los parámetros de a los que se *puede llamar*.  

\ *Extraargs*
Los argumentos que se reenvían de la ruta a la que se *puede llamar* junto con el tipo de evento coincidente.

### <a name="return-value"></a>Valor devuelto

Valor **booleano** que es **true** si la coincidencia se realizó correctamente, o **false** en caso contrario.

## <a name="remarks"></a>Comentarios

Los tipos de evento que se van a usar para los parámetros *TEvent* y *TEvents* se seleccionan de una lista de *clases de captura*. Para obtener una lista de eventos y las clases de captura que puede usar para hacerlos coincidir, consulte [tabla de eventos](../event-table.md).

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
