---
title: MatchEventStackInMemberFunction
description: La C++ referencia de la función MATCHEVENTSTACKINMEMBERFUNCTION del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStackInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a966ea5209a25a62c08cb0873d0565299a15d27
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334371"
---
# <a name="matcheventstackinmemberfunction"></a>MatchEventStackInMemberFunction

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `MatchEventStackInMemberFunction` se usa para hacer coincidir una pila de eventos con una jerarquía de eventos concreta, que se describe en la lista de parámetros de una función miembro. Las jerarquías coincidentes se reenvían a la función miembro para su posterior procesamiento. Para obtener más información sobre eventos, pilas de eventos y jerarquías, vea [tabla de eventos](../event-table.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, TExtraParams...),
    TExtraArgs&&...           extraArgs);

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, TExtraParams...),
    TExtraArgs&&...           extraArgs);

// Etc...

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename     T3,
    typename     T4,
    typename     T5,
    typename     T6,
    typename     T7,
    typename     T8,
    typename     T9,
    typename     T10,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, TExtraParams...),
    TExtraArgs&&...           extraArgs);
```

### <a name="parameters"></a>Parámetros

\ *TInterface*
Tipo que contiene la función miembro.

\ *TReturn*
El tipo de valor devuelto de la función miembro.

*T1*,...,\ *T10*
Tipos que describen la jerarquía de eventos que se va a comparar.

\ *TExtraParams*
Los tipos de los parámetros adicionales aceptados por la función miembro y los tipos de jerarquía de eventos.

\ *TExtraArgs*
Tipos de los argumentos adicionales que se pasaron a `MatchEventStackInMemberFunction`.

\ *eventStack*
Pila de eventos que debe coincidir con la jerarquía de tipos de evento descrita por *T1* a *T10*.

\ *objectPtr*
Un puntero a un objeto en el que se llama a *memberFunc* .

\ *memberFunc*
Función miembro que describe la jerarquía de tipos de evento que debe coincidir.

\ *Extraargs*
Los argumentos que se reenvían de la ruta a *memberFunc* junto con los parámetros de la jerarquía de tipos de evento.

### <a name="return-value"></a>Valor devuelto

Valor **booleano** que es **true** si la coincidencia se realizó correctamente, o **false** en caso contrario.

## <a name="remarks"></a>Comentarios

El último evento de *eventStack* siempre coincide con la última entrada de la jerarquía de tipos de evento para que coincida. Todos los demás tipos de la jerarquía de tipos de evento pueden coincidir con cualquier posición en *eventStack* excepto en la última, siempre que estén en el mismo orden.

Los tipos de evento que se van a usar para los parámetros *T1* a *T10* se seleccionan de una lista de *clases de captura*. Para obtener una lista de eventos y las clases de captura que puede usar para hacerlos coincidir, consulte [tabla de eventos](../event-table.md).

## <a name="example"></a>Ejemplo

```cpp
void MyClass::Foo1(Compiler cl, BackEndPass bep, C2DLL c2,
    CodeGeneration cg, Thread t, Function f) { }

void MyClass::Foo2(Compiler cl, Function f) { }

void MyClass::Foo3(Thread t, Compiler cl, Function f) { }

void MyClass::Foo4(Compiler cl) { }

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo1);

    bool b2 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo2);

    bool b3 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo3);

    bool b4 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo4);

    // b1: true because the parameter types of Foo1 match the eventStack
    //     exactly.
    // b2: true because Function is the last entry in both the member
    //     function parameter list and 'eventStack', and also because
    //     Compiler comes before Function in 'eventStack' and in the
    //     parameter type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', the member function parameter
    //     list doesn't list them in the right order.
    // b4: false because the last entry in the member function parameter
    //     list is Compiler, which doesn't match the last entry in 'eventStack'
    //     (Function).
}
```

::: moniker-end
