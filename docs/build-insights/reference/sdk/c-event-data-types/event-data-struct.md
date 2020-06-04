---
title: estructura EVENT_DATA
description: El SDK de C++ Build Insights EVENT_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8ce396febe278c5e7c34fe170939c9522913f92a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325606"
---
# <a name="event_data-structure"></a>estructura EVENT_DATA

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `EVENT_DATA` estructura describe un evento recibido de una sesión de análisis o recorrección. Estas sesiones se inician llamando a las funciones [Analizar](../functions/analyze.md), [AnalizarA](../functions/analyze-a.md), [AnalizarW](../functions/analyze-w.md), [Relog,](../functions/relog.md) [RelogA](../functions/relog-a.md)o [RelogW.](../functions/relog-w.md)

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct EVENT_DATA_TAG
{
    unsigned short          EventId;
    unsigned long long      EventInstanceId;

    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;
    long long               ExclusiveDurationTicks;
    long long               CPUTicks;
    long long               ExclusiveCPUTicks;
    long long               WallClockTimeResponsibilityTicks;
    long long               ExclusiveWallClockTimeResponsibilityTicks;

    const void*             Data;

    unsigned long           ProcessId;
    unsigned long           ThreadId;
    unsigned short          ProcessorIndex;

    const char*             EventName;
    const wchar_t*          EventWideName;

} EVENT_DATA;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `EventId` | Número que identifica el evento. Para obtener una lista de identificadores de eventos, vea [EVENT_ID](event-id-enum.md). |
| `EventInstanceId` | Número que identifica de forma única el evento actual dentro de un seguimiento. Este valor no cambia al analizar o volver a registrar el mismo seguimiento varias veces. Utilice este campo para identificar el mismo evento en varios pasos de análisis o relogging sobre el mismo seguimiento. |
| `TickFrequency` | El número de ticks por segundo que se utilizarán al evaluar una duración medida en ticks. |
| `StartTimestamp` | Cuando el evento es una *actividad,* este campo se establece en un valor de tick capturado en el momento en que se inició la actividad. Si este evento es un *evento simple,* este campo se establece en un valor de tick capturado en el momento en que se produjo el evento. |
| `StopTimestamp` | Cuando el evento es una *actividad,* este campo se establece en un valor de tick capturado en el momento en que se detuvo la actividad. Si el evento stop aún no se ha recibido para esta actividad, este campo se establece en cero. Si este evento es un *evento simple,* este campo se establece en cero. |
| `ExclusiveDurationTicks` | Si este evento es una *actividad*, este campo se establece en el número de ticks que se produjeron directamente en esta actividad. Se excluye el número de ticks que se produjeron en una actividad secundaria. Este campo se establece en cero para *Eventos simples*. |
| `CPUTicks` | Si este evento es una *actividad,* este campo se establece en el número de ticks de CPU que se produjeron durante esta actividad. Un tick de CPU es diferente de un tick normal. Los ticks de CPU solo se cuentan cuando la CPU está ejecutando código en una actividad. Los ticks de CPU no se cuentan cuando el subproceso asociado a la actividad está en suspensión. Este campo se establece en cero para *Eventos simples*. |
| `ExclusiveCPUTicks` | Este campo tiene el `CPUTicks`mismo significado que , excepto que no incluye los ticks de CPU que se produjeron en las actividades infantiles. Este campo se establece en cero para *Eventos simples*. |
| `WallClockTimeResponsibilityTicks` | Si este evento es una *actividad*, este campo se establece en un recuento de ticks que representa la contribución de esta actividad a la hora general del reloj de pared. Un tick de responsabilidad de tiempo de reloj de pared es diferente de un tick normal. Las garrapatas de responsabilidad de tiempo de reloj de pared tienen en cuenta el paralelismo entre las actividades. Por ejemplo, dos actividades paralelas pueden tener una duración de 50 ticks y la misma hora de inicio y parada. En este caso, a ambos se les asignará una responsabilidad de tiempo de reloj de pared de 25 ticks. Este campo se establece en cero para *Eventos simples*. |
| `ExclusiveWallClockTimeResponsibilityTicks` | Este campo tiene el `WallClockTimeResponsibilityTicks`mismo significado que , excepto que no incluye los ticks de responsabilidad de tiempo de reloj de pared de las actividades de los niños. Este campo se establece en cero para *Eventos simples*. |
| `Data` | Apunta a datos adicionales almacenados en el evento. El tipo de datos a los que `EventId` se señala es diferente, dependiendo del campo. |
| `ProcessId` | Identificador del proceso en el que se produjo el evento. |
| `ThreadId` | Identificador del subproceso en el que se produjo el evento. |
| `ProcessorIndex` | El número de CPU indexado a cero en el que se produjo el evento. |
| `EventName` | Cadena ANSI que contiene el nombre `EventId`de la entidad identificada por . |
| `EventWideName` | Cadena amplia que contiene el nombre `EventId`de la entidad identificada por . |

## <a name="remarks"></a>Observaciones

Muchos campos `EVENT_DATA` en contienen recuentos de ticks. C++ Build Insights utiliza el contador de rendimiento de Window como fuente de ticks. Se debe utilizar un `TickFrequency` recuento de ticks con el campo para convertirlo en una unidad de tiempo adecuada, como segundos. Consulte el ejemplo siguiente para realizar esta conversión. `EVENT_DATA`no contiene un campo para el recuento regular de ticks de una actividad. Para obtener este `StartTimestamp` valor, reste de `StopTimestamp`. `EVENT_DATA`es una estructura que está destinada a ser utilizada por los usuarios de la API de C. Para los usuarios de la API de C++, clases como [Event](../cpp-event-data-types/event.md) do time conversions automáticamente.

El valor `EVENT_DATA` `Data` del campo depende del `EventId` valor de su campo. El valor `Data` de se describe en la tabla siguiente. Es posible que falten algunos identificadores de entidad en la tabla siguiente. En este caso, el `Data` `nullptr` campo se establece en o cero.

| Valor de `EventId` | Tipo señalado por`Data` |
|--|--|
| `EVENT_ID_BACK_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_COMMAND_LINE` | `const wchar_t` |
| `EVENT_ID_COMPILER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_ENVIRONMENT_VARIABLE` | [NAME_VALUE_PAIR_DATA](name-value-pair-data-struct.md) |
| `EVENT_ID_EXECUTABLE_IMAGE_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_EXP_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FILE_INPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FORCE_INLINE` | [FUNCTION_FORCE_INLINEE_DATA](function-force-inlinee-data-struct.md) |
| `EVENT_ID_FRONT_END_FILE` | [FRONT_END_FILE_DATA](front-end-file-data-struct.md) |
| `EVENT_ID_FRONT_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_FUNCTION` | [FUNCTION_DATA](function-data-struct.md) |
| `EVENT_ID_IMP_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LINKER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_OBJ_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_SYMBOL_NAME` | [SYMBOL_NAME_DATA](symbol-name-data-struct.md) |
| `EVENT_ID_TEMPLATE_INSTANTIATION` | [TEMPLATE_INSTANTIATION_DATA](template-instantiation-data-struct.md) |

## <a name="tick-conversion-example"></a>Ejemplo de conversión de ticks

```cpp
//
// We have the elapsed number of ticks, along with the
// number of ticks per second. We use these values
// to convert to the number of elapsed microseconds.
// To guard against loss-of-precision, we convert
// to microseconds *before* dividing by ticks-per-second.
//

long long ConvertDurationToMicroseconds(const sruct EVENT_DATA& eventData)
{
    long long duration = eventData.StopTimestamp - eventData.StartTimestamp;
    long long duration *= 1000000;
    return duration / eventData.TickFrequency;
}
```

::: moniker-end
