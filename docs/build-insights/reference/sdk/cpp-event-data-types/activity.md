---
title: Clase de la actividad
description: La referencia de clase de actividad del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Activity
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2ea04150aec9c0b2366d97e6e4c15de557a4f47c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325247"
---
# <a name="activity-class"></a>Clase de la actividad

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `Activity` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con cualquier evento de actividad. Consulte la [tabla](../event-table.md) de eventos para ver todos `Activity` los eventos que puede coincidir con la clase.

## <a name="syntax"></a>Sintaxis

```cpp
class Activity : public Event
{
public:
    Activity(const RawEvent& event);

    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;
    const long long& ExclusiveDurationTicks() const;
    const long long& CPUTicks() const;
    const long long& ExclusiveCPUTicks() const;
    const long long& WallClockTimeResponsibilityTicks() const;
    const long long& ExclusiveWallClockTimeResponsibilityTicks() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>Observaciones

Varias funciones `Activity` miembro de la clase devuelven un recuento de ticks. C++ Build Insights utiliza el contador de rendimiento de Windows como fuente de ticks. Se debe utilizar un recuento de ticks con una frecuencia de ticks para convertirlo en una unidad de tiempo como segundos. La `TickFrequency` función miembro, disponible en la clase base [Event,](event.md) se puede llamar para obtener la frecuencia de tick. La página [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) muestra un ejemplo de conversión de ticks en una unidad de tiempo.

Si no desea convertir ticks en unidades `Activity` de tiempo usted mismo, la clase proporciona funciones miembro que devuelven valores de tiempo en nanosegundos. Utilice la biblioteca `chrono` C++ estándar para convertirlas en otras unidades de tiempo.

## <a name="members"></a>Miembros

Junto con sus miembros heredados `Activity` de la clase base [Event,](event.md) la clase contiene los siguientes miembros:

### <a name="constructor"></a>Constructor

[Actividad](#activity)

### <a name="functions"></a>Functions

[CPUTicks](#cpu-ticks)\
[CPUTime](#cpu-time)\
[Duración](#duration)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp](#stop-timestamp)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="activity"></a><a name="activity"></a> Actividad

```cpp
Activity(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Cualquier evento de actividad.

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

## <a name="duration"></a><a name="duration"></a>Duración

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Valor devuelto

La duración de la actividad en nanosegundos.

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

Un recuento de ticks que representa la contribución de esta actividad al tiempo general del reloj de pared. Un tick de responsabilidad de tiempo de reloj de pared es diferente de un tick normal. Las garrapatas de responsabilidad de tiempo de reloj de pared tienen en cuenta el paralelismo entre las actividades. Dos actividades paralelas pueden tener una duración de 50 ticks, y la misma hora de inicio y parada. En este caso, a ambos se les asigna una responsabilidad de tiempo de reloj de pared de 25 ticks.

::: moniker-end
