---
title: Clase EventStack
description: Referencia C++ de la clase EVENTSTACK del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6da2fd25082399b82d788c5d119a39e2f7388714
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334899"
---
# <a name="eventstack-class"></a>Clase EventStack

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `EventStack` es una colección de objetos de [evento](event.md) . Todos los eventos recibidos del C++ SDK de Build Insights tienen el formato de un objeto de `EventStack`. La última entrada de esta pila es el evento que se está procesando actualmente. Las entradas que preceden a la última entrada son la jerarquía primaria del evento actual. Para obtener más información sobre el modelo de eventos C++ que se usa en Build Insights, consulte [tabla de eventos](../event-table.md).

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

### <a name="functions"></a>Funciones

[Back](#back)
[operador []](#subscript-operator)
[tamaño](#size)

## <a name="back"></a>Atrás

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto [RawEvent](raw-event.md) que representa la última entrada de la pila. La última entrada en una pila de eventos es el evento que se desencadenó.

## <a name="event-stack"></a>EventStack

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>Parámetros

\ de *datos*
Datos sin procesar a partir de los cuales se compila el `EventStack`.

### <a name="remarks"></a>Comentarios

Normalmente no es necesario construir `EventStack` objetos. Los proporciona el C++ SDK de Build Insights cuando se procesan eventos durante una sesión de análisis o de registro.

## <a name="subscript-operator"></a>operador []

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>Parámetros

*índice*\
Índice del elemento al que se va a obtener acceso en la pila de eventos.

### <a name="return-value"></a>Valor devuelto

Objeto [RawEvent](raw-event.md) que representa el evento almacenado en la posición indicada por el *Índice* en la pila de eventos.

## <a name="size"></a>Ajusta

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Valor devuelto

Tamaño de la pila de eventos.

::: moniker-end
