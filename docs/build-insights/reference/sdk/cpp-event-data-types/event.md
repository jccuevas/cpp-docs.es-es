---
title: Clase de eventos
description: Referencia C++ de la clase de eventos SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 205a4e0ca9dd9449933f38f02d4ceafd5df8ead2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334893"
---
# <a name="event-class"></a>Clase de eventos

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `Event` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con cualquier evento.

## <a name="syntax"></a>Sintaxis

```cpp
class Event
{
public:
    Event(const RawEvent& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             Timestamp() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;
};
```

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

[Evento](#entity)

### <a name="functions"></a>Funciones

[Data](#data)
[EventID](#event-id)\
\ [EventInstanceId](#event-instance-id)
[EventName](#event-name)\
\ [EventWideName](#event-wide-name)
[ProcessId](#process-id)\
\ [ProcessorIndex](#processor-index)
\ [ThreadId](#thread-id)
\ [TickFrequency](#tick-frequency)
[Timestamp](#timestamp)

## <a name="entity"></a>Ceso

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Cualquier evento.

## <a name="data"></a>Data

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a los datos adicionales contenidos en este evento. Para obtener más información sobre cómo interpretar este campo, vea [EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="event-id"></a>EventId

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>Valor devuelto

Número que identifica el tipo de evento. Para obtener una lista de identificadores de eventos, vea [EVENT_ID](../c-event-data-types/event-id-enum.md).

## <a name="event-instance-id"></a>EventInstanceId

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>Valor devuelto

Número que identifica de forma única el evento dentro de un seguimiento. Este valor no cambia cuando se analiza varias veces el mismo seguimiento o el registro del mismo. Utilice este valor para identificar el mismo evento en varios análisis o para que el registro pase por el mismo seguimiento.

## <a name="event-name"></a>EventName

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>Valor devuelto

Cadena ANSI que contiene el nombre del tipo de evento identificado por [EventID](#event-id).

## <a name="event-wide-name"></a>EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>Valor devuelto

Cadena de tipo ancho que contiene el nombre del evento identificado por [EventID](#event-id).

## <a name="process-id"></a>ProcessId

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del proceso en el que se produjo el evento.

## <a name="processor-index"></a>ProcessorIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>Valor devuelto

Índice de base cero del procesador lógico en el que se produjo el evento.

## <a name="thread-id"></a>ThreadId

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del subproceso en el que se produjo el evento.

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Valor devuelto

Número de TICs por segundo que se van a usar al evaluar una duración medida en pasos para este evento.

## <a name="timestamp"></a>Indicaciones

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>Valor devuelto

Si el evento es una actividad, esta función devuelve un valor de tick capturado en el momento en que se inició la actividad. Para un evento simple, esta función devuelve un valor de tick capturado en el momento en que se produjo el evento.

::: moniker-end
