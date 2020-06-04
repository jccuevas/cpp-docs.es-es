---
title: Clase IRelogger
description: Referencia de clase IRelogger del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 146377b2b44df43ed4b2f749efd9fb614a2a09c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329156"
---
# <a name="irelogger-class"></a>Clase IRelogger

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `IRelogger` clase proporciona una interfaz para volver a registrar un seguimiento de seguimiento de eventos para Windows (ETW). Se utiliza con las funciones [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md) y [MakeStaticReloggerGroup.](../functions/make-static-analyzer-group.md) Utilícelo `IRelogger` como clase base para crear su propio registrador que pueda formar parte de un grupo de reregistradores.

## <a name="syntax"></a>Sintaxis

```cpp
class IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
    virtual AnalysisControl OnBeginRelogging();
    virtual AnalysisControl OnEndRelogging();
    virtual AnalysisControl OnBeginReloggingPass();
    virtual AnalysisControl OnEndReloggingPass() ;

    virtual ~IRelogger();
};
```

## <a name="remarks"></a>Observaciones

El valor devuelto predeterminado para todas las `AnalysisControl::CONTINUE`funciones que no se invalidan es . Para obtener más información, vea [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Miembros

### <a name="destructor"></a>Destructor

[•IRelogger](#irelogger-destructor)

### <a name="functions"></a>Functions

[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)\
[OnTraceInfo](#on-trace-info)

## <a name="irelogger"></a><a name="irelogger-destructor"></a>•IRelogger

Destruye la clase IRelogger.

```cpp
virtual ~IRelogger();
```

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a>OnBeginRelogging

Esta función se llama antes de que comience el paso de recorrección.

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>Valor devuelto

Código [AnalysisControl](analysis-control-enum-class.md) que describe lo que debe suceder a continuación.

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

Esta función se llama al principio del paso de recorrección.

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>Valor devuelto

Código [AnalysisControl](analysis-control-enum-class.md) que describe lo que debe suceder a continuación.

## <a name="onendrelogging"></a><a name="on-end-relogging"></a>OnEndRelogging

Esta función se llama después de que el pase de reregistro haya finalizado.

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>Valor devuelto

Código [AnalysisControl](analysis-control-enum-class.md) que describe lo que debe suceder a continuación.

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a>OnEndReloggingPass

Esta función se llama al final del paso de relogging.

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>Valor devuelto

Código [AnalysisControl](analysis-control-enum-class.md) que describe lo que debe suceder a continuación.

## <a name="onsimpleevent"></a><a name="on-simple-event"></a>OnSimpleEvent

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

Se llama a esta función cuando se procesa un evento simple.

### <a name="parameters"></a>Parámetros

*eventStack*\
La pila de eventos para este evento simple. Para obtener más información sobre las pilas de eventos, consulte [Eventos](../event-table.md).

### <a name="return-value"></a>Valor devuelto

Código [AnalysisControl](analysis-control-enum-class.md) que describe lo que debe suceder a continuación.

## <a name="onstartactivity"></a><a name="on-start-activity"></a>OnStartActivity

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

Se llama a esta función cuando se procesa un evento de inicio de actividad.

### <a name="parameters"></a>Parámetros

*eventStack*\
La pila de eventos para este evento de inicio de actividad. Para obtener más información sobre las pilas de eventos, consulte [Eventos](../event-table.md).

### <a name="return-value"></a>Valor devuelto

Código [AnalysisControl](analysis-control-enum-class.md) que describe lo que debe suceder a continuación.

## <a name="onstopactivity"></a><a name="on-stop-activity"></a>OnStopActivity

Se llama a esta función cuando se procesa un evento de detención de actividad.

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>Parámetros

*eventStack*\
La pila de eventos para este evento de detención de actividad. Para obtener más información sobre las pilas de eventos, consulte [Eventos](../event-table.md).

### <a name="return-value"></a>Valor devuelto

Código [AnalysisControl](analysis-control-enum-class.md) que describe lo que debe suceder a continuación.

## <a name="ontraceinfo"></a><a name="on-trace-info"></a>OnTraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

Esta función se llama una vez al principio de cada paso de análisis o relogging.

### <a name="parameters"></a>Parámetros

*traceInfo*\
Un [TraceInfo](../cpp-event-data-types/trace-info.md) objeto que contiene propiedades útiles sobre el seguimiento que se consume.

### <a name="return-value"></a>Valor devuelto

Código [AnalysisControl](analysis-control-enum-class.md) que describe lo que debe suceder a continuación.

::: moniker-end
