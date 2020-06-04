---
title: Clase EventStack
description: Referencia de clase EventStack del SDK de Compilación de C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eaaaedcbf57fdaf8e437a80a7823488febac3e1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324980"
---
# <a name="eventstack-class"></a>Clase EventStack

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `EventStack` clase es una colección de [Event](event.md) objetos. Todos los eventos recibidos del SDK de C++ Build Insights vienen en forma de objeto. `EventStack` La última entrada de esta pila es el evento que se está procesando actualmente. Las entradas que preceden a la última entrada son la jerarquía primaria del evento actual. Para obtener más información sobre el modelo de eventos utilizado en C++ Build Insights, vea tabla de [eventos](../event-table.md).

## <a name="syntax"></a>Sintaxis

```cpp
class EventStack
{
public:
    EventStack(const EVENT_COLLECTION_DATA& data);

    size_t      Size() const;
    RawEvent    Back() const;
    RawEvent    operator[] (size_t index) const;
};
```

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

[EventStack](#event-stack)

### <a name="functions"></a>Functions

[Operador](#back)
[trasero[]](#subscript-operator)
[Tamaño](#size)

## <a name="back"></a><a name="back"></a>Atrás

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto [RawEvent](raw-event.md) que representa la última entrada de la pila. La última entrada de una pila de eventos es el evento que se desencadenó.

## <a name="eventstack"></a><a name="event-stack"></a>EventStack

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>Parámetros

*Datos*\
Los datos sin `EventStack` procesar a partir de los cuales se compila.

### <a name="remarks"></a>Observaciones

Normalmente no es necesario `EventStack` construir objetos usted mismo. El SDK de C++ Build Insights se proporciona cuando se procesan eventos durante una sesión de análisis o reshaber.

## <a name="operator"></a><a name="subscript-operator"></a>operador[]

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>Parámetros

*Índice*\
El índice del elemento al que se va a tener acceso en la pila de eventos.

### <a name="return-value"></a>Valor devuelto

Objeto [RawEvent](raw-event.md) que representa el evento almacenado en la posición indicada por *index* en la pila de eventos.

## <a name="size"></a>Tamaño de la <a name="size"></a>

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño de la pila de eventos.

::: moniker-end
