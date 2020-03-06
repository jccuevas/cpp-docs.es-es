---
title: MatchEventInMemberFunction
description: La C++ referencia de la función MATCHEVENTINMEMBERFUNCTION del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eabbb8a91609b1447ebcc19af32df2ffed347c24
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334383"
---
# <a name="matcheventinmemberfunction"></a>MatchEventInMemberFunction

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `MatchEventInMemberFunction` se usa para hacer coincidir un evento con el tipo descrito por el primer parámetro de una función miembro. El evento coincidente se reenvía a la función miembro para su posterior procesamiento.

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

\ *TInterface*
Tipo que contiene la función miembro.

\ *TReturn*
El tipo de valor devuelto de la función miembro.

\ *TEvent*
Tipo del evento que se va a comparar.

\ *TExtraParams*
Tipos de los parámetros adicionales aceptados por la función miembro junto con el tipo de evento que debe coincidir.

\ *TExtraArgs*
Tipos de los argumentos adicionales que se pasaron a `MatchEventInMemberFunction`.

*event*\
Evento que se va a comparar con el tipo de evento descrito por *TEvent*.

\ *objectPtr*
Un puntero a un objeto en el que se llama a *memberFunc* .

\ *memberFunc*
Función miembro que describe el tipo de evento que debe coincidir.

\ *Extraargs*
Los argumentos que se reenvían de la ruta a *memberFunc* junto con el parámetro de tipo de evento.

### <a name="return-value"></a>Valor devuelto

Valor **booleano** que es **true** si la coincidencia se realizó correctamente, o **false** en caso contrario.

## <a name="remarks"></a>Comentarios

El tipo de evento que se va a usar para el parámetro *TEvent* se puede seleccionar en una lista de *clases de captura*. Para obtener una lista de eventos y las clases de captura que puede usar para hacerlos coincidir, consulte [tabla de eventos](../event-table.md).

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
