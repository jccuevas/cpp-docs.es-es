---
title: Clase TraceInfo
description: Referencia C++ de la clase TRACEINFO del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5cf32c8dc954a803a11888231d35b1050ac81cc3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334503"
---
# <a name="traceinfo-class"></a>Clase TraceInfo

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `TraceInfo` se utiliza para tener acceso a propiedades útiles sobre un seguimiento que se está analizando o reregistrando.

## <a name="syntax"></a>Sintaxis

```cpp
class TraceInfo
{
public:
    TraceInfo(const TRACE_INFO_DATA& data);

    const unsigned long& LogicalProcessorCount() const;

    const long long& TickFrequency() const;
    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;

    std::chrono::nanoseconds Duration() const;
};
```

## <a name="remarks"></a>Comentarios

Reste el `StartTimestamp` de `StopTimestamp` para obtener el número de pasos transcurridos durante todo el seguimiento. Utilice `TickFrequency` para convertir el valor resultante en una unidad de tiempo. Para obtener un ejemplo de cómo convertir TICs en Time, vea [EVENT_DATA](../c-event-data-types/event-data-struct.md).

Si no desea convertir los tics por su cuenta, la clase `TraceInfo` proporciona una función miembro que devuelve la duración del seguimiento en nanosegundos. Use la biblioteca C++ de `chrono` estándar para convertir este valor en otras unidades de tiempo.

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

[TraceInfo](#trace-info)

### <a name="functions"></a>Funciones

[Duration](#duration)
[LogicalProcessorCount](#logical-processor-count)
[StartTimestamp](#start-timestamp)
[StopTimestamp](#stop-timestamp)
[TickFrequency](#tick-frequency)

## <a name="duration"></a>Duration

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Valor devuelto

La duración de la actividad en nanosegundos.

## <a name="logical-processor-count"></a>LogicalProcessorCount

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de procesadores lógicos en el equipo en el que se recopiló el seguimiento.

## <a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de tick capturado en el momento en que se inició el seguimiento.

## <a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de tick capturado en el momento en que se detuvo el seguimiento.

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Valor devuelto

Número de TICs por segundo que se van a usar al evaluar una duración medida en pasos.

## <a name="trace-info"></a>TraceInfo

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>Parámetros

\ de *datos*
Datos que contienen la información sobre el seguimiento.

::: moniker-end
