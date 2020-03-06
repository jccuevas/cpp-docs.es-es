---
title: Clase de la actividad
description: Referencia C++ de clase de actividad del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Activity
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6de411c375b42e4acfb44bf0fac9d28ad57f1ca7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335031"
---
# <a name="activity-class"></a>Clase de la actividad

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `Activity` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con cualquier evento de actividad. Consulte la [tabla de eventos](../event-table.md) para ver todos los eventos que pueden coincidir con la clase `Activity`.

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

## <a name="remarks"></a>Comentarios

Varias funciones miembro de la clase `Activity` devuelven un recuento de pasos. C++Build Insights usa el contador de rendimiento de Windows como un origen de TICs. Un recuento de pasos debe usarse con una frecuencia de graduación para convertirla en una unidad de tiempo como segundos. Se puede llamar a la función miembro `TickFrequency`, disponible en la clase base de [evento](event.md) , para obtener la frecuencia de la marca de graduación. En la página [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) se muestra un ejemplo de conversión de TICs en una unidad de tiempo.

Si no desea convertir los tics en las unidades de tiempo, la clase `Activity` proporciona funciones miembro que devuelven valores de hora en nanosegundos. Use la biblioteca C++ de `chrono` estándar para convertirlas en otras unidades de tiempo.

## <a name="members"></a>Miembros

Junto con sus miembros heredados de la clase base de [evento](event.md) , la clase `Activity` contiene los siguientes miembros:

### <a name="constructor"></a>Constructor

[Actividad](#activity)

### <a name="functions"></a>Funciones

\ [CPUTicks](#cpu-ticks)
\ [CPUTime](#cpu-time)
[Duración](#duration)\
\ [ExclusiveCPUTicks](#exclusive-cpu-ticks)
\ [ExclusiveCPUTime](#exclusive-cpu-time)
\ [ExclusiveDuration](#exclusive-duration)
\ [ExclusiveDurationTicks](#exclusive-duration-ticks)
\ [ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)
\ [ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)
\ [StartTimestamp](#start-timestamp)
\ [StopTimestamp](#stop-timestamp)
\ [WallClockTimeResponsibility](#wall-clock-time-responsibility)
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="activity"></a>Proceso

```cpp
Activity(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Cualquier evento de actividad.

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

## <a name="duration"></a>Duration

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Valor devuelto

La duración de la actividad en nanosegundos.

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
