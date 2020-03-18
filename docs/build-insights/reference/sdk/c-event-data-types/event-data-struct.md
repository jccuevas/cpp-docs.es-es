---
title: Estructura de EVENT_DATA
description: El C++ SDK de Build insights EVENT_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 572cbdaba346ddb77b665b5677b978c83a80aa3d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422911"
---
# <a name="event_data-structure"></a>Estructura de EVENT_DATA

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura `EVENT_DATA` describe un evento recibido de una sesión de análisis o de registro. Estas sesiones se inician mediante una llamada a las funciones [Analyze](../functions/analyze.md), [analyzea](../functions/analyze-a.md), [AnalyzeW](../functions/analyze-w.md), [relog](../functions/relog.md), [RelogA](../functions/relog-a.md)o [RelogW](../functions/relog-w.md) .

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

## <a name="members"></a>Members

|  |  |
|--|--|
| `EventId` | Número que identifica el evento. Para obtener una lista de identificadores de eventos, vea [EVENT_ID](event-id-enum.md). |
| `EventInstanceId` | Número que identifica de forma única el evento actual dentro de un seguimiento. Este valor no cambia cuando se analiza varias veces el mismo seguimiento o el registro del mismo. Utilice este campo para identificar el mismo evento en varios análisis o para que el registro pase sobre el mismo seguimiento. |
| `TickFrequency` | Número de TICs por segundo que se van a usar al evaluar una duración medida en pasos. |
| `StartTimestamp` | Cuando el evento es una *actividad*, este campo se establece en un valor de tick capturado en el momento en que se inició la actividad. Si este evento es un *evento simple*, este campo se establece en un valor de tick capturado en el momento en que se produjo el evento. |
| `StopTimestamp` | Cuando el evento es una *actividad*, este campo se establece en un valor de tick capturado en el momento en que se detuvo la actividad. Si el evento de detención todavía no se ha recibido para esta actividad, este campo se establece en cero. Si este evento es un *evento simple*, este campo se establece en cero. |
| `ExclusiveDurationTicks` | Si este evento es una *actividad*, este campo se establece en el número de pasos que se produjeron directamente en esta actividad. Se excluye el número de pasos que se produjeron en una actividad secundaria. Este campo se establece en cero para *los eventos simples*. |
| `CPUTicks` | Si este evento es una *actividad*, este campo se establece en el número de TICs de CPU que se produjeron durante esta actividad. Una marca de la CPU es diferente de una marca normal. Los tics de CPU solo se cuentan cuando la CPU ejecuta código en una actividad. Los tics de CPU no se cuentan cuando el subproceso asociado a la actividad está en suspensión. Este campo se establece en cero para *los eventos simples*. |
| `ExclusiveCPUTicks` | Este campo tiene el mismo significado que `CPUTicks`, salvo que no incluye los tics de CPU que se produjeron en las actividades secundarias. Este campo se establece en cero para *los eventos simples*. |
| `WallClockTimeResponsibilityTicks` | Si este evento es una *actividad*, este campo se establece en un contador que representa la contribución de esta actividad a la hora general del reloj de la pared. Un paso de responsabilidad de reloj en la pared es diferente de un TIC normal. Los tics de responsabilidad de reloj en la pared tienen en cuenta el paralelismo entre las actividades. Por ejemplo, dos actividades paralelas pueden tener una duración de 50 TICs y la misma hora de inicio y detención. En este caso, se asignará a ambos una responsabilidad de tiempo de reloj de 25 TICs. Este campo se establece en cero para *los eventos simples*. |
| `ExclusiveWallClockTimeResponsibilityTicks` | Este campo tiene el mismo significado que `WallClockTimeResponsibilityTicks`, salvo que no incluye los tics de responsabilidad de tiempo de reloj de la pared de las actividades secundarias. Este campo se establece en cero para *los eventos simples*. |
| `Data` | Apunta a datos adicionales almacenados en el evento. El tipo de datos señalado es diferente, dependiendo del campo `EventId`. |
| `ProcessId` | Identificador del proceso en el que se produjo el evento. |
| `ThreadId` | Identificador del subproceso en el que se produjo el evento. |
| `ProcessorIndex` | Número de CPU con índice cero en el que se produjo el evento. |
| `EventName` | Cadena ANSI que contiene el nombre de la entidad identificada por `EventId`. |
| `EventWideName` | Cadena de tipo ancho que contiene el nombre de la entidad identificada por `EventId`. |

## <a name="remarks"></a>Observaciones

Muchos campos de `EVENT_DATA` contienen recuentos de pasos. C++Build Insights usa el contador de rendimiento de la ventana como un origen de TICs. Se debe usar un recuento de pasos con el campo `TickFrequency` para convertirlo en una unidad de tiempo adecuada, como segundos. Vea el ejemplo siguiente para realizar esta conversión. `EVENT_DATA` no contiene un campo para el recuento de pasos normal de una actividad. Para obtener este valor, reste `StartTimestamp` de `StopTimestamp`. `EVENT_DATA` es una estructura que está pensada para que la usen los usuarios de la API de C. En C++ el caso de los usuarios de la API, las clases como [eventos](../cpp-event-data-types/event.md) realizan conversiones de tiempo automáticamente.

El valor de `EVENT_DATA` campo `Data` depende del valor de su campo `EventId`. El valor de `Data` se describe en la tabla siguiente. Algunos identificadores de entidad pueden faltar en la tabla siguiente. En este caso, el campo de `Data` se establece en `nullptr` o en cero.

| Valor de `EventId` | Tipo al que apunta `Data` |
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

## <a name="tick-conversion-example"></a>Ejemplo de conversión de tick

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
