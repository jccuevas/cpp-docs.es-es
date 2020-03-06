---
title: Clase RawEvent
description: Referencia C++ de la clase RAWEVENT del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4088920d6070e14d64ccd046238c1c49b2556ea1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334605"
---
# <a name="rawevent-class"></a>Clase RawEvent

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `RawEvent` se usa para representar un evento general en un [EventStack](event-stack.md).

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

## <a name="remarks"></a>Comentarios

Varias funciones miembro de la clase `RawEvent` devuelven un recuento de pasos. C++Build Insights usa el contador de rendimiento de Windows como un origen de TICs. Un recuento de pasos debe usarse con una frecuencia de marca para convertirla en una unidad de tiempo como segundos. Se puede llamar a la función miembro `TickFrequency` para obtener la frecuencia de la marca de graduación. Vea la página [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) para obtener un ejemplo sobre cómo convertir TICs en una unidad de tiempo.

Si no desea convertir los tics por su cuenta, la clase `RawEvent` proporciona funciones miembro que devuelven valores de hora en nanosegundos. Use la biblioteca C++ de `chrono` estándar para convertir nanosegundos en otras unidades de tiempo.

## <a name="members"></a>Miembros

### <a name="constructor"></a>Constructor

[RawEvent](#raw-event)

### <a name="functions"></a>Funciones

\ [CPUTicks](#cpu-ticks)
\ [CPUTime](#cpu-time)
[Datos](#data)\
[Duración](#duration)\
[EventId](#event-id)
[EventInstanceId](#event-instance-id)
[eventName](#event-name)\
\ [EventWideName](#event-wide-name)
\ [ExclusiveCPUTicks](#exclusive-cpu-ticks)
\ [ExclusiveCPUTime](#exclusive-cpu-time)
\ [ExclusiveDuration](#exclusive-duration)
\ [ExclusiveDurationTicks](#exclusive-duration-ticks)
\ [ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)
\ [ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)
[ProcessId](#process-id)\
\ [ProcessorIndex](#processor-index)
\ [StartTimestamp](#start-timestamp)
\ [StopTimestamp](#stop-timestamp)
\ [ThreadId](#thread-id)
\ [TickFrequency](#tick-frequency)
\ [WallClockTimeResponsibility](#wall-clock-time-responsibility)
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="raw-event"></a>RawEvent

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>Parámetros

*event*\
Datos del evento.

## <a name="cpu-ticks"></a>CPUTicks

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>Valor devuelto

El número de TICs de CPU que se produjeron durante esta actividad. Una marca de la CPU es diferente de una marca normal. Los tics de CPU solo se cuentan cuando la CPU ejecuta código en una actividad. Los tics de CPU no se cuentan cuando el subproceso asociado a la actividad está en suspensión.

## <a name="cpu-time"></a>CPUTime

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>Valor devuelto

La cantidad de tiempo que la CPU estaba ejecutando código dentro de esta actividad. Este valor puede ser mayor que la duración de la actividad si las actividades secundarias se ejecutan en subprocesos independientes. El valor se devuelve en nanosegundos.

## <a name="data"></a>Data

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a los datos adicionales contenidos en este evento. Para obtener más información sobre cómo interpretar este campo, vea [EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="duration"></a>Duration

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Valor devuelto

La duración de la actividad en nanosegundos.

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

Cadena ancha que contiene el nombre del tipo de evento identificado por [EventID](#event-id).

## <a name="exclusive-cpu-ticks"></a>ExclusiveCPUTicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>Valor devuelto

Igual que [CPUTicks](#cpu-ticks), pero sin incluir los tics de la CPU que se produjeron en las actividades secundarias.

## <a name="exclusive-cpu-time"></a>ExclusiveCPUTime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>Valor devuelto

Igual que [CPUTime](#cpu-time), salvo que no se incluye el tiempo de CPU de las actividades secundarias.

## <a name="exclusive-duration"></a>ExclusiveDuration

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>Valor devuelto

La duración de la actividad en nanosegundos, sin incluir la cantidad de tiempo dedicado a las actividades secundarias.

## <a name="exclusive-duration-ticks"></a>ExclusiveDurationTicks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>Valor devuelto

El número de pasos que se produjeron en esta actividad, excepto el número de pasos que se produjeron en las actividades secundarias.

## <a name="exclusive-wall-clock-time-responsibility"></a>ExclusiveWallClockTimeResponsibility

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Valor devuelto

Igual que [WallClockTimeResponsibility](#wall-clock-time-responsibility), pero sin incluir la responsabilidad de la hora de la pared de las actividades secundarias.

## <a name="exclusive-wall-clock-time-responsibility-ticks"></a>ExclusiveWallClockTimeResponsibilityTicks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Valor devuelto

Igual que [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks), pero sin incluir los tics de responsabilidad de la hora de reloj de la pared de las actividades secundarias.

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

## <a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de tick capturado en el momento en que se inició la actividad.

## <a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de tick capturado en el momento en que se detuvo la actividad.

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

## <a name="wall-clock-time-responsibility"></a>WallClockTimeResponsibility

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Valor devuelto

La responsabilidad en el reloj de la pared de esta actividad, en nanosegundos. Para obtener más información sobre qué significa la responsabilidad de la hora del reloj, vea [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks).

## <a name="wall-clock-time-responsibility-ticks"></a>WallClockTimeResponsibilityTicks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Valor devuelto

Recuento de pasos que representa la contribución de esta actividad a la hora general del reloj de la pared. Un paso de responsabilidad de reloj en la pared es diferente de un TIC normal. Los tics de responsabilidad de reloj en la pared tienen en cuenta el paralelismo entre las actividades. Dos actividades paralelas pueden tener una duración de 50 TICs y la misma hora de inicio y detención. En este caso, Get asigna una responsabilidad de tiempo de reloj de 25 TICs.

::: moniker-end
