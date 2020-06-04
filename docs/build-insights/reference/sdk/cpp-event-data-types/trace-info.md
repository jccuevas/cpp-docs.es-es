---
title: Clase TraceInfo
description: La referencia de la clase TraceInfo del SDK de Compilación de C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 75d53937e3999f5692dee0ecf419e0ce5f49a274
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324172"
---
# <a name="traceinfo-class"></a>Clase TraceInfo

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `TraceInfo` clase se utiliza para tener acceso a propiedades útiles sobre un seguimiento que se está analizando o reregistrando.

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

## <a name="remarks"></a>Observaciones

Restar `StartTimestamp` `StopTimestamp` el para obtener el número de ticks transcurridos durante todo el seguimiento. Se `TickFrequency` utiliza para convertir el valor resultante en una unidad de tiempo. Para obtener un ejemplo de conversión de ticks a tiempo, consulte [EVENT_DATA](../c-event-data-types/event-data-struct.md).

Si no desea convertir los ticks `TraceInfo` usted mismo, la clase proporciona una función miembro que devuelve la duración del seguimiento en nanosegundos. Utilice la biblioteca `chrono` C++ estándar para convertir este valor en otras unidades de tiempo.

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

[TraceInfo](#trace-info)

### <a name="functions"></a>Functions

[Duración](#duration)
[LogicalProcessorCount](#logical-processor-count)
[StartTimestamp](#start-timestamp)
[StopTimestamp](#stop-timestamp)
[TickFrequency](#tick-frequency)

## <a name="duration"></a><a name="duration"></a>Duración

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Valor devuelto

La duración de la actividad en nanosegundos.

## <a name="logicalprocessorcount"></a><a name="logical-processor-count"></a>LogicalProcessorCount

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de procesadores lógicos en la máquina donde se recopiló el seguimiento.

## <a name="starttimestamp"></a><a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de tick capturado en el momento en que se inició el seguimiento.

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de tick capturado en el momento en que se detuvo el seguimiento.

## <a name="tickfrequency"></a><a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Valor devuelto

El número de ticks por segundo que se utilizarán al evaluar una duración medida en ticks.

## <a name="traceinfo"></a><a name="trace-info"></a>TraceInfo

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>Parámetros

*Datos*\
Los datos que contienen la información sobre el seguimiento.

::: moniker-end
