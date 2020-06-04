---
title: MatchEventStackInMemberFunction
description: Referencia de la función MatchEventStackInMemberFunction del SDK de compilación de C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStackInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28842a02e7edc2e00266d8c7941798f4ce714ded
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323885"
---
# <a name="matcheventstackinmemberfunction"></a>MatchEventStackInMemberFunction

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `MatchEventStackInMemberFunction` función se utiliza para hacer coincidir una pila de eventos con una jerarquía de eventos específica, descrita por la lista de parámetros de una función miembro. Las jerarquías coincidentes se reenvían a la función miembro para su posterior procesamiento. Para obtener más información sobre eventos, pilas de eventos y jerarquías, consulte Tabla de [eventos](../event-table.md).

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

*TInterface*\
El tipo que contiene la función miembro.

*TReturn*\
El tipo de valor devuelto de la función miembro.

*T1*, ..., *T10*\
Los tipos que describen la jerarquía de eventos que se va a hacer coincidir.

*TExtraParams*\
Los tipos de los parámetros adicionales aceptados por la función miembro y los tipos de jerarquía de eventos.

*TExtraArgs*\
Los tipos de los argumentos `MatchEventStackInMemberFunction`adicionales que se pasaron a .

*eventStack*\
La pila de eventos que debe coincidir con la jerarquía de tipos de evento descrita por *T1* a *T10.*

*objectPtr*\
Puntero a un objeto en el que se llama a *memberFunc.*

*memberFunc*\
La función miembro que describe la jerarquía de tipos de evento que se va a coincidir.

*extraArgs*\
Los argumentos que se reenvían perfectamente a *memberFunc* junto con los parámetros de jerarquía de tipo de evento.

### <a name="return-value"></a>Valor devuelto

Un valor **bool** que es **true** si la coincidencia se realizó correctamente, o **false** en caso contrario.

## <a name="remarks"></a>Observaciones

El último evento de *eventStack* siempre coincide con la última entrada de la jerarquía de tipos de evento que debe coincidir. Todos los demás tipos de la jerarquía de tipos de evento pueden coincidir con cualquier posición de *eventStack* excepto la última, siempre que estén en el mismo orden.

Los tipos de eventos que se van a utilizar para los parámetros *T1* a *T10* se seleccionan de una lista de clases de *captura.* Para obtener una lista de eventos y las clases de captura que puede usar para hacer coincidirlos, consulte [la tabla](../event-table.md)de eventos .

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
