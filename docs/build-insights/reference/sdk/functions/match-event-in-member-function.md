---
title: MatchEventInMemberFunction
description: Referencia de la función MatchEventInMemberFunction del SDK de Compilación de C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 522630da16e3f4a1294316d88140f4bc25dca2c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323896"
---
# <a name="matcheventinmemberfunction"></a>MatchEventInMemberFunction

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `MatchEventInMemberFunction` función se utiliza para hacer coincidir un evento con el tipo descrito por el primer parámetro de una función miembro. El evento coincidente se reenvía a la función miembro para su posterior procesamiento.

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     TEvent,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventInMemberFunction(
    const RawEvent&          event,
    TInterface*              objectPtr,
    TReturn (TInterface::*   memberFunc)(TEvent, TExtraParams...),
    TExtraArgs&&...          extraArgs);
```

### <a name="parameters"></a>Parámetros

*TInterface*\
El tipo que contiene la función miembro.

*TReturn*\
El tipo de valor devuelto de la función miembro.

*TEvent*\
El tipo del evento que se debe hacer coincidir.

*TExtraParams*\
Los tipos de los parámetros adicionales aceptados por la función miembro junto con el tipo de evento que se debe coincidir.

*TExtraArgs*\
Los tipos de los argumentos `MatchEventInMemberFunction`adicionales que se pasaron a .

*Evento*\
Evento que se va a hacer coincidir con el tipo de evento descrito por *TEvent*.

*objectPtr*\
Puntero a un objeto en el que se llama a *memberFunc.*

*memberFunc*\
La función miembro que describe el tipo de evento que se va a coincidir.

*extraArgs*\
Los argumentos que se reenvían perfectamente a *memberFunc* junto con el parámetro de tipo de evento.

### <a name="return-value"></a>Valor devuelto

Un valor **bool** que es **true** si la coincidencia se realizó correctamente, o **false** en caso contrario.

## <a name="remarks"></a>Observaciones

El tipo de evento que se va a utilizar para el parámetro *TEvent* se puede seleccionar de una lista de clases de *captura.* Para obtener una lista de eventos y las clases de captura que puede usar para hacer coincidirlos, consulte [la tabla](../event-table.md)de eventos .

## <a name="example"></a>Ejemplo

```cpp
void MyClass::Foo1(Function f) {}

void MyClass::Foo2(Compiler cl) {}

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo1);

    bool b2 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo2);

    // b1: true because the first parameter of Foo1 is Function.
    // b2: false because the first parameter of Foo2 isn't Function.
}
```

::: moniker-end
