---
title: Clase RawEvent
description: Referencia de la clase RawEvent del SDK de Compilación de C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 83629457ac3a0d1f991f6b084af2f3400612b2ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324380"
---
# <a name="rawevent-class"></a>Clase RawEvent

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `RawEvent` clase se utiliza para representar un evento general en un [EventStack](event-stack.md).

## <a name="syntax"></a>Sintaxis

```cpp
class RawEvent
{
public:
    RawEvent(const EVENT_DATA& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             StartTimestamp() const;
    const long long&             StopTimestamp() const;
    const long long&             ExclusiveDurationTicks() const;
    const long long&             CPUTicks() const;
    const long long&             ExclusiveCPUTicks() const;
    const long long&             WallClockTimeResponsibilityTicks() const;
    const long long&             ExclusiveWallClockTimeResponsibilityTicks() const;
    const void*                  Data() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>Observaciones

Varias funciones `RawEvent` miembro de la clase devuelven un recuento de ticks. C++ Build Insights utiliza el contador de rendimiento de Windows como fuente de ticks. Se debe utilizar un recuento de ticks con una frecuencia de ticks para convertirlo en una unidad de tiempo como segundos. Se `TickFrequency` puede llamar a la función miembro para obtener la frecuencia de tick. Consulte la página [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) para obtener un ejemplo sobre cómo convertir ticks en una unidad de tiempo.

Si no desea convertir los ticks `RawEvent` usted mismo, la clase proporciona funciones miembro que devuelven valores de tiempo en nanosegundos. Utilice la biblioteca `chrono` C++ estándar para convertir nanosegundos en otras unidades de tiempo.

## <a name="members"></a>Miembros

### <a name="constructor"></a>Constructor

[RawEvent](#raw-event)

### <a name="functions"></a>Functions

[CPUTicks](#cpu-ticks)\
[CPUTime](#cpu-time)\
[Datos](#data)\
[Duración](#duration)\
[EventId](#event-id)
[EventInstanceId](#event-instance-id)
[EventName](#event-name)\
[EventWideName](#event-wide-name)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[ProcessId](#process-id)\
[ProcessorIndex](#processor-index)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp](#stop-timestamp)\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="rawevent"></a><a name="raw-event"></a>RawEvent

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Datos del evento.

## <a name="cputicks"></a><a name="cpu-ticks"></a>CPUTicks

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>Valor devuelto

El número de ticks de CPU que se produjeron durante esta actividad. Un tick de CPU es diferente de un tick normal. Los ticks de CPU solo se cuentan cuando la CPU está ejecutando código en una actividad. Los ticks de CPU no se cuentan cuando el subproceso asociado a la actividad está en suspensión.

## <a name="cputime"></a><a name="cpu-time"></a>CPUTime

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>Valor devuelto

La cantidad de tiempo que la CPU estaba ejecutando código dentro de esta actividad. Este valor puede ser mayor que la duración de la actividad si las actividades secundarias se ejecutan en subprocesos independientes. El valor se devuelve en nanosegundos.

## <a name="data"></a><a name="data"></a>Datos

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a datos adicionales contenidos en este evento. Para obtener más información sobre cómo interpretar este campo, consulte [EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="duration"></a><a name="duration"></a>Duración

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Valor devuelto

La duración de la actividad en nanosegundos.

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

Cadena amplia que contiene el nombre del tipo de evento identificado por [EventId](#event-id).

## <a name="exclusivecputicks"></a><a name="exclusive-cpu-ticks"></a>ExclusiveCPUTicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>Valor devuelto

Igual que [CPUTicks](#cpu-ticks), pero sin incluir los ticks de CPU que se produjeron en las actividades secundarias.

## <a name="exclusivecputime"></a><a name="exclusive-cpu-time"></a>ExclusiveCPUTime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>Valor devuelto

Igual que [CPUTime](#cpu-time), excepto que no se incluye el tiempo de CPU de las actividades secundarias.

## <a name="exclusiveduration"></a><a name="exclusive-duration"></a>ExclusiveDuration

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>Valor devuelto

La duración de la actividad en nanosegundos, sin incluir la cantidad de tiempo que se pasó en las actividades infantiles.

## <a name="exclusivedurationticks"></a><a name="exclusive-duration-ticks"></a>ExclusiveDurationTicks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>Valor devuelto

El número de ticks que se produjeron en esta actividad, excluyendo el número de ticks que se produjeron en las actividades secundarias.

## <a name="exclusivewallclocktimeresponsibility"></a><a name="exclusive-wall-clock-time-responsibility"></a>ExclusiveWallClockTimeResponsibility

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Valor devuelto

Igual que [WallClockTimeResponsibility](#wall-clock-time-responsibility), pero sin incluir la responsabilidad de la hora del reloj de pared de las actividades secundarias.

## <a name="exclusivewallclocktimeresponsibilityticks"></a><a name="exclusive-wall-clock-time-responsibility-ticks"></a>ExclusiveWallClockTimeResponsibilityTicks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Valor devuelto

Igual que [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks), pero sin incluir los ticks de responsabilidad de tiempo de reloj de pared de las actividades secundarias.

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

## <a name="starttimestamp"></a><a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de tick capturado en el momento en que se inició la actividad.

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de tick capturado en el momento en que se detuvo la actividad.

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

## <a name="wallclocktimeresponsibility"></a><a name="wall-clock-time-responsibility"></a>WallClockTimeResponsibility

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Valor devuelto

La responsabilidad del tiempo del reloj de pared de esta actividad, en nanosegundos. Para obtener más información sobre lo que significa la responsabilidad de tiempo de reloj de pared, vea [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks).

## <a name="wallclocktimeresponsibilityticks"></a><a name="wall-clock-time-responsibility-ticks"></a>WallClockTimeResponsibilityTicks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Valor devuelto

Un recuento de ticks que representa la contribución de esta actividad al tiempo general del reloj de pared. Un tick de responsabilidad de tiempo de reloj de pared es diferente de un tick normal. Las garrapatas de responsabilidad de tiempo de reloj de pared tienen en cuenta el paralelismo entre las actividades. Dos actividades paralelas pueden tener una duración de 50 ticks y el mismo tiempo de inicio y parada. En este caso, a ambos se les asigna una responsabilidad de tiempo de reloj de pared de 25 ticks.

::: moniker-end
