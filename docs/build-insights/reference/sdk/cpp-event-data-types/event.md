---
title: Clase de evento
description: La referencia de clase de eventos del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 25d58f642a1c314e48ddff62553394bcc65e4717
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324965"
---
# <a name="event-class"></a>Clase de evento

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `Event` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con cualquier evento.

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

### <a name="functions"></a>Functions

[Data](#data)
[EventId](#event-id)\
[EventInstanceId](#event-instance-id)\
[Eventname](#event-name)\
[EventWideName](#event-wide-name)\
[ProcessId](#process-id)\
[ProcessorIndex](#processor-index)\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency)\
[Timestamp](#timestamp)

## <a name="event"></a>o<a name="entity"></a>

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Cualquier evento.

## <a name="data"></a><a name="data"></a>Datos

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a datos adicionales contenidos en este evento. Para obtener más información sobre cómo interpretar este campo, consulte [EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="eventid"></a><a name="event-id"></a>Eventid

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>Valor devuelto

Número que identifica el tipo de evento. Para obtener una lista de identificadores de eventos, vea [EVENT_ID](../c-event-data-types/event-id-enum.md).

## <a name="eventinstanceid"></a><a name="event-instance-id"></a>EventInstanceId

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>Valor devuelto

Número que identifica de forma única el evento dentro de un seguimiento. Este valor no cambia al analizar o volver a registrar el mismo seguimiento varias veces. Utilice este valor para identificar el mismo evento en varios pasos de análisis o relogging sobre el mismo seguimiento.

## <a name="eventname"></a><a name="event-name"></a>Eventname

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>Valor devuelto

Cadena ANSI que contiene el nombre del tipo de evento identificado por [EventId](#event-id).

## <a name="eventwidename"></a><a name="event-wide-name"></a>EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>Valor devuelto

Cadena amplia que contiene el nombre del evento identificado por [EventId](#event-id).

## <a name="processid"></a><a name="process-id"></a>ProcessId

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del proceso en el que se produjo el evento.

## <a name="processorindex"></a><a name="processor-index"></a>ProcessorIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>Valor devuelto

El índice de base cero para el procesador lógico en el que se produjo el evento.

## <a name="threadid"></a><a name="thread-id"></a>ThreadId

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del subproceso en el que se produjo el evento.

## <a name="tickfrequency"></a><a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Valor devuelto

El número de ticks por segundo que se utilizarán al evaluar una duración medida en ticks para este evento.

## <a name="timestamp"></a><a name="timestamp"></a>Timestamp

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>Valor devuelto

Si el evento es una actividad, esta función devuelve un valor de tick capturado en el momento en que se inició la actividad. Para un evento simple, esta función devuelve un valor de tick capturado en el momento en que se produjo el evento.

::: moniker-end
