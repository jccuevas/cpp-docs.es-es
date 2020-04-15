---
title: estructura TRACE_INFO_DATA
description: El SDK de C++ Build Insights TRACE_INFO_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 70ae17a376f79cad7a669d81e482f551afd0ec62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325275"
---
# <a name="trace_info_data-structure"></a>estructura TRACE_INFO_DATA

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `TRACE_INFO_DATA` estructura describe un seguimiento que se está analizando o reregistrando.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct TRACE_INFO_DATA_TAG
{
    unsigned long           LogicalProcessorCount;
    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;

} TRACE_INFO_DATA;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `LogicalProcessorCount` | El número de procesadores lógicos en la máquina donde se recopiló el seguimiento. |
| `TickFrequency` | El número de ticks por segundo que se utilizarán al evaluar una duración medida en ticks. |
| `StartTimestamp` | Este campo se establece en un valor de tick capturado en el momento en que se inició el seguimiento. |
| `StopTimestamp` | Este campo se establece en un valor de tick capturado en el momento en que se detuvo el seguimiento. |

## <a name="remarks"></a>Observaciones

`StartTimestamp` Restar `StopTimestamp` de para obtener el número de ticks transcurridos durante todo el seguimiento. Se `TickFrequency` utiliza para convertir el valor resultante en una unidad de tiempo. Para obtener un ejemplo que convierte ticks en unidades de tiempo, consulte [EVENT_DATA](event-data-struct.md).

::: moniker-end
