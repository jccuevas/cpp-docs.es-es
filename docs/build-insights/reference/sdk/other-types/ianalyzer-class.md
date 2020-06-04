---
title: Clase IAnalyzer
description: Referencia de clase IAnalyzer del SDK de C++Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: be9d80bb94450458c73fd6ce8d908985ba6f293d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329172"
---
# <a name="ianalyzer-class"></a>Clase IAnalyzer

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `IAnalyzer` clase proporciona una interfaz para analizar un seguimiento de seguimiento de eventos para Windows (ETW). Se utiliza con las funciones [MakeDynamicAnalyzerGroup](../functions/make-dynamic-analyzer-group.md), [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md), [MakeStaticAnalyzerGroup](../functions/make-dynamic-analyzer-group.md)y [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) . Utilícelo `IAnalyzer` como clase base para crear su propio analizador que pueda formar parte de un analizador o grupo de registrador.

## <a name="syntax"></a>Sintaxis

```cpp
class IAnalyzer : public IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
    virtual AnalysisControl OnStopActivity(const EventStack& eventStack)
    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
    virtual AnalysisControl OnBeginAnalysis();
    virtual AnalysisControl OnEndAnalysis();
    virtual AnalysisControl OnBeginAnalysisPass();
    virtual AnalysisControl OnEndAnalysisPass();

    AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnBeginRelogging() final;
    AnalysisControl OnEndRelogging() final;
    AnalysisControl OnBeginReloggingPass() final;
    AnalysisControl OnEndReloggingPass() final;

    virtual ~IAnalyzer();
};
```

## <a name="remarks"></a>Observaciones

Las clases `IAnalyzer` que derivan de se pueden utilizar como analizadores y reloggers. Cuando se utiliza como registradores, las funciones específicas del registrador redirigen a su equivalente de analizador. Lo contrario no es cierto: una `IRelogger` clase que deriva de no se puede usar como analizador. El uso de un analizador en un grupo de relogger es un patrón común. Cuando se coloca en una posición temprana de un grupo de reregistradores, un analizador puede precalcular información y ponerla a disposición de los remaderos en posiciones posteriores.

El valor devuelto predeterminado para todas las `AnalysisControl::CONTINUE`funciones que no se invalidan es . Para obtener más información, vea [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Miembros

Además del miembro [OnTraceInfo](irelogger-class.md#on-trace-info) de la `IRelogger` interfaz, la `IAnalyzer` clase contiene los siguientes miembros:

### <a name="destructor"></a>Destructor

[•IAnalyzer](#ianalyzer-destructor)

### <a name="functions"></a>Functions

[OnBeginAnalysis](#on-begin-analysis)\
[OnBeginAnalysisPass](#on-begin-analysis-pass)\
[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndAnalysis](#on-end-analysis)\
[OnEndAnalysisPass](#on-end-analysis-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)

## <a name="ianalyzer"></a><a name="ianalyzer-destructor"></a>•IAnalyzer

Destruye la clase IAnalyzer.

```cpp
virtual ~IAnalyzer();
```

## <a name="onbeginanalysis"></a><a name="on-begin-analysis"></a>OnBeginAnalysis

Para los analizadores que forman parte de un grupo de analizadores, se llama a esta función antes de que comience el primer paso de análisis. Para los analizadores que forman parte de un grupo de relogger, se llama a esta función antes de que comience el paso de relogging. Para los analizadores que forman parte del grupo de analizadores y reregistradores de la misma sesión de recorrección, esta función se llama dos veces antes de que comience el primer paso de análisis.

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>Valor devuelto

Código [AnalysisControl](analysis-control-enum-class.md) que describe lo que debe suceder a continuación.

## <a name="onbeginanalysispass"></a><a name="on-begin-analysis-pass"></a>OnBeginAnalysisPass

Para los analizadores que forman parte de un grupo de analizadores, se llama a esta función al principio de cada paso de análisis. Para los analizadores que forman parte de un grupo de reregistradores, se llama a esta función al principio del paso del registrador. Para los analizadores que forman parte del grupo de analizador y reregistrador de la misma sesión de recorrección, esta función se llama al principio de cada paso de análisis y al principio del pase de reregistrador.

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>Valor devuelto

Código [AnalysisControl](analysis-control-enum-class.md) que describe lo que debe suceder a continuación.

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a>OnBeginRelogging

```cpp
AnalysisControl OnBeginRelogging() final;
```

Esta función no se puede invalidar. Lo llama el SDK de C++ Build Insights cuando un analizador forma parte de un grupo de reregistradores. Esta función redirige la llamada a [OnBeginAnalysis](#on-begin-analysis).

### <a name="return-value"></a>Valor devuelto

El resultado de la llamada [OnBeginAnalysis.](#on-begin-analysis)

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

Esta función no se puede invalidar. Lo llama el SDK de C++ Build Insights cuando un analizador forma parte de un grupo de reregistradores. Esta función redirige la llamada a [OnBeginAnalysisPass](#on-begin-analysis-pass).

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>Valor devuelto

El resultado de la llamada [OnBeginAnalysisPass.](#on-begin-analysis-pass)

## <a name="onendanalysis"></a><a name="on-end-analysis"></a>OnEndAnalysis

Para los analizadores que forman parte de un grupo de analizadores, se llama a esta función una vez finalizado el último paso de análisis. Para los analizadores que forman parte de un grupo de reregistrador, se llama a esta función una vez finalizado el paso de reregistro. Para los analizadores que forman parte del analizador y del grupo de reaqueder de la misma sesión de recorrección, esta función se llama dos veces:

1. después de que todos los pases de análisis han terminado y antes de que comience el paso de relogging, y
1. después de que el pase de relogging haya terminado.

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>Valor devuelto

Código [AnalysisControl](analysis-control-enum-class.md) que describe lo que debe suceder a continuación.

## <a name="onendanalysispass"></a><a name="on-end-analysis-pass"></a>OnEndAnalysisPass

Para los analizadores que forman parte de un grupo de analizadores, se llama a esta función al final de cada paso de análisis. Para los analizadores que forman parte de un grupo de relogger, se llama a esta función al final del paso del registrador. Para los analizadores que forman parte del analizador y del grupo de relogger de la misma sesión de relogging, esta función se llama al final de cada paso de análisis y al final del pase del relogger.

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>Valor devuelto

Código [AnalysisControl](analysis-control-enum-class.md) que describe lo que debe suceder a continuación.

## <a name="onendrelogging"></a><a name="on-end-relogging"></a>OnEndRelogging

Esta función no se puede invalidar. Lo llama el SDK de C++ Build Insights cuando un analizador forma parte de un grupo de reregistradores. Esta función redirige la llamada a [OnEndAnalysis](#on-end-analysis).

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>Valor devuelto

El resultado de la llamada [OnEndAnalysis.](#on-end-analysis)

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a>OnEndReloggingPass

Esta función no se puede invalidar. Lo llama el SDK de C++ Build Insights cuando un analizador forma parte de un grupo de reregistradores. Esta función redirige la llamada a [OnEndAnalysisPass](#on-end-analysis-pass).

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>Valor devuelto

El resultado de la llamada [OnEndAnalysisPass.](#on-end-analysis-pass)

## <a name="onsimpleevent"></a><a name="on-simple-event"></a>OnSimpleEvent

Se llama a esta función cuando se procesa un evento simple. La segunda versión de esta función no se puede invalidar. Lo llama el SDK de C++ Build Insights cuando un analizador forma parte de un grupo de reregistradores. Todas las llamadas a la versión 2 se redirigen a la versión 1.

### <a name="version-1"></a>versión 1

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

### <a name="version-2"></a>versión 2

```cpp
AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Parámetros

*eventStack*\
La pila de eventos para este evento simple. Para obtener más información sobre las pilas de eventos, consulte [Eventos](../event-table.md).

*relogSession*\
Este parámetro no se utiliza.

### <a name="return-value"></a>Valor devuelto

Código [AnalysisControl](analysis-control-enum-class.md) que describe lo que debe suceder a continuación.

## <a name="onstartactivity"></a><a name="on-start-activity"></a>OnStartActivity

Se llama a esta función cuando se procesa un evento de inicio de actividad. La segunda versión de esta función no se puede invalidar. Lo llama el SDK de C++ Build Insights cuando un analizador forma parte de un grupo de reregistradores. Todas las llamadas a la versión 2 se redirigen a la versión 1.

### <a name="version-1"></a>versión 1

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>versión 2

```cpp
AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Parámetros

*eventStack*\
La pila de eventos para este evento de inicio de actividad. Para obtener más información sobre las pilas de eventos, consulte [Eventos](../event-table.md).

*relogSession*\
Este parámetro no se utiliza.

### <a name="return-value"></a>Valor devuelto

Código [AnalysisControl](analysis-control-enum-class.md) que describe lo que debe suceder a continuación.

## <a name="onstopactivity"></a><a name="on-stop-activity"></a>OnStopActivity

Se llama a esta función cuando se procesa un evento de detención de actividad. La segunda versión de esta función no se puede invalidar. Lo llama el SDK de C++ Build Insights cuando un analizador forma parte de un grupo de reregistradores. Todas las llamadas a la versión 2 se redirigen a la versión 1.

### <a name="version-1"></a>versión 1

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>versión 2

```cpp
AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Parámetros

*eventStack*\
La pila de eventos para este evento de detención de actividad. Para obtener más información sobre las pilas de eventos, consulte [Eventos](../event-table.md).

*relogSession*\
Este parámetro no se utiliza.

### <a name="return-value"></a>Valor devuelto

Código [AnalysisControl](analysis-control-enum-class.md) que describe lo que debe suceder a continuación.

::: moniker-end
