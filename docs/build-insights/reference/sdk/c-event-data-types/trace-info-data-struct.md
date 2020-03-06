---
title: Estructura de TRACE_INFO_DATA
description: El C++ SDK de Build insights TRACE_INFO_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 04cb5c013bca8879507983d169b38e5af0f1322b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335055"
---
# <a name="trace_info_data-structure"></a>Estructura de TRACE_INFO_DATA

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura `TRACE_INFO_DATA` describe un seguimiento que se está analizando o reregistrando.

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
| `LogicalProcessorCount` | El número de procesadores lógicos en el equipo en el que se recopiló el seguimiento. |
| `TickFrequency` | Número de TICs por segundo que se van a usar al evaluar una duración medida en pasos. |
| `StartTimestamp` | Este campo se establece en un valor de tick capturado en el momento en que se inició el seguimiento. |
| `StopTimestamp` | Este campo se establece en un valor de tick capturado en el momento en que se detuvo el seguimiento. |

## <a name="remarks"></a>Comentarios

Reste `StartTimestamp` de `StopTimestamp` para obtener el número de pasos transcurridos durante todo el seguimiento. Utilice `TickFrequency` para convertir el valor resultante en una unidad de tiempo. Para obtener un ejemplo en el que se convierten TICs en unidades de tiempo, vea [EVENT_DATA](event-data-struct.md).

::: moniker-end
