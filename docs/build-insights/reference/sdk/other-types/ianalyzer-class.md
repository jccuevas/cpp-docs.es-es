---
title: Clase IAnalyzer
description: Referencia C++ de la clase IANALYZER del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 53f7b36695bb24d96ccfe88afbb56ff717c94dc9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334083"
---
# <a name="ianalyzer-class"></a>Clase IAnalyzer

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `IAnalyzer` proporciona una interfaz para analizar un seguimiento de seguimiento de eventos para Windows (ETW). Se usa con las funciones [MakeDynamicAnalyzerGroup](../functions/make-dynamic-analyzer-group.md), [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md), [MakeStaticAnalyzerGroup](../functions/make-dynamic-analyzer-group.md)y [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) . Use `IAnalyzer` como una clase base para crear su propio analizador que puede formar parte de un grupo de analizador o de reregistrador.

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

## <a name="remarks"></a>Comentarios

Las clases que derivan de `IAnalyzer` se pueden usar como analizadores y reregistradores. Cuando se usan como reregistradores, las funciones específicas del reregistrador redirigen a su analizador equivalente. Lo contrario no es cierto: una clase que deriva de `IRelogger` no se puede usar como analizador. El uso de un analizador en un grupo de reregistrador es un patrón común. Cuando se coloca en una posición temprana de un grupo de reregistradores, un analizador puede calcular previamente la información y hacer que esté disponible para los reregistradores en posiciones posteriores.

El valor devuelto predeterminado para todas las funciones que no se reemplazan es `AnalysisControl::CONTINUE`. Para obtener más información, vea [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Miembros

Además del miembro [OnTraceInfo](irelogger-class.md#on-trace-info) de la interfaz `IRelogger`, la clase `IAnalyzer` contiene los siguientes miembros:

### <a name="destructor"></a>Destructor

[~ IAnalyzer](#ianalyzer-destructor)

### <a name="functions"></a>Funciones

\ [OnBeginAnalysis](#on-begin-analysis)
\ [OnBeginAnalysisPass](#on-begin-analysis-pass)
\ [OnBeginRelogging](#on-begin-relogging)
\ [OnBeginReloggingPass](#on-begin-relogging-pass)
\ [OnEndAnalysis](#on-end-analysis)
\ [OnEndAnalysisPass](#on-end-analysis-pass)
\ [OnEndRelogging](#on-end-relogging)
\ [OnEndReloggingPass](#on-end-relogging-pass)
\ [OnSimpleEvent](#on-simple-event)
\ [OnStartActivity](#on-start-activity)
[OnStopActivity](#on-stop-activity)

## <a name="ianalyzer-destructor"></a>~ IAnalyzer

Destruye la clase IAnalyzer.

```cpp
virtual ~IAnalyzer();
```

## <a name="on-begin-analysis"></a>OnBeginAnalysis

En el caso de los analizadores que forman parte de un grupo de Analyzer, se llama a esta función antes de comenzar la primera fase de análisis. En el caso de los analizadores que forman parte de un grupo de reregistradores, se llama a esta función antes de que empiece el paso de registro. En el caso de los analizadores de la misma sesión de reregistro, se llama a esta función dos veces antes de comenzar la primera fase de análisis.

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>Valor devuelto

Código de [AnalysisControl](analysis-control-enum-class.md) que describe lo que debería pasar a continuación.

## <a name="on-begin-analysis-pass"></a>OnBeginAnalysisPass

En el caso de los analizadores que forman parte de un grupo de Analyzer, esta función se llama al principio de cada paso del análisis. En el caso de los analizadores que forman parte de un grupo de reregistradores, se llama a esta función al principio del paso del registro. En el caso de los analizadores de la misma sesión de reregistro, se llama a esta función al principio de cada fase de análisis y al principio del paso de reregistrador.

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>Valor devuelto

Código de [AnalysisControl](analysis-control-enum-class.md) que describe lo que debería pasar a continuación.

## <a name="on-begin-relogging"></a>OnBeginRelogging

```cpp
AnalysisControl OnBeginRelogging() final;
```

Esta función no se puede invalidar. Lo llama el C++ SDK de Build Insights cuando un analizador forma parte de un grupo de reregistradores. Esta función redirige la llamada a [OnBeginAnalysis](#on-begin-analysis).

### <a name="return-value"></a>Valor devuelto

Resultado de la llamada a [OnBeginAnalysis](#on-begin-analysis) .

## <a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

Esta función no se puede invalidar. Lo llama el C++ SDK de Build Insights cuando un analizador forma parte de un grupo de reregistradores. Esta función redirige la llamada a [OnBeginAnalysisPass](#on-begin-analysis-pass).

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>Valor devuelto

Resultado de la llamada a [OnBeginAnalysisPass](#on-begin-analysis-pass) .

## <a name="on-end-analysis"></a>OnEndAnalysis

En el caso de los analizadores que forman parte de un grupo de Analyzer, se llama a esta función una vez finalizada la última fase de análisis. En el caso de los analizadores que forman parte de un grupo de reregistradores, se llama a esta función una vez finalizada la fase de reregistro. En el caso de los analizadores que forman parte del grupo de analizador y de reregistrador de la misma sesión de reregistro, esta función se llama dos veces:

1. una vez finalizados todos los pasos de análisis y antes de que comience el paso de registro, y
1. una vez finalizado el paso de registro.

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>Valor devuelto

Código de [AnalysisControl](analysis-control-enum-class.md) que describe lo que debería pasar a continuación.

## <a name="on-end-analysis-pass"></a>OnEndAnalysisPass

En el caso de los analizadores que forman parte de un grupo de Analyzer, esta función se llama al final de cada fase de análisis. En el caso de los analizadores que forman parte de un grupo de reregistradores, esta función se llama al final del paso de reregistrador. En el caso de los analizadores de la misma sesión de reregistro, se llama a esta función al final de cada paso del análisis y al final del paso del reregistrador.

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>Valor devuelto

Código de [AnalysisControl](analysis-control-enum-class.md) que describe lo que debería pasar a continuación.

## <a name="on-end-relogging"></a>OnEndRelogging

Esta función no se puede invalidar. Lo llama el C++ SDK de Build Insights cuando un analizador forma parte de un grupo de reregistradores. Esta función redirige la llamada a [OnEndAnalysis](#on-end-analysis).

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>Valor devuelto

Resultado de la llamada a [OnEndAnalysis](#on-end-analysis) .

## <a name="on-end-relogging-pass"></a>OnEndReloggingPass

Esta función no se puede invalidar. Lo llama el C++ SDK de Build Insights cuando un analizador forma parte de un grupo de reregistradores. Esta función redirige la llamada a [OnEndAnalysisPass](#on-end-analysis-pass).

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>Valor devuelto

Resultado de la llamada a [OnEndAnalysisPass](#on-end-analysis-pass) .

## <a name="on-simple-event"></a>OnSimpleEvent

Se llama a esta función cuando se está procesando un evento simple. No se puede reemplazar la segunda versión de esta función. Lo llama el C++ SDK de Build Insights cuando un analizador forma parte de un grupo de reregistradores. Todas las llamadas a la versión 2 se redirigen a la versión 1.

### <a name="version-1"></a>versión 1

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

### <a name="version-2"></a>Versión 2

```cpp
AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Parámetros

\ *eventStack*
Pila de eventos para este evento simple. Para obtener más información sobre las pilas de eventos, vea [eventos](../event-table.md).

\ *relogSession*
Este parámetro no se utiliza.

### <a name="return-value"></a>Valor devuelto

Código de [AnalysisControl](analysis-control-enum-class.md) que describe lo que debería pasar a continuación.

## <a name="on-start-activity"></a>OnStartActivity

Se llama a esta función cuando se está procesando un evento de inicio de actividad. No se puede reemplazar la segunda versión de esta función. Lo llama el C++ SDK de Build Insights cuando un analizador forma parte de un grupo de reregistradores. Todas las llamadas a la versión 2 se redirigen a la versión 1.

### <a name="version-1"></a>versión 1

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>Versión 2

```cpp
AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Parámetros

\ *eventStack*
Pila de eventos para este evento de inicio de actividad. Para obtener más información sobre las pilas de eventos, vea [eventos](../event-table.md).

\ *relogSession*
Este parámetro no se utiliza.

### <a name="return-value"></a>Valor devuelto

Código de [AnalysisControl](analysis-control-enum-class.md) que describe lo que debería pasar a continuación.

## <a name="on-stop-activity"></a>OnStopActivity

Se llama a esta función cuando se está procesando un evento de detención de actividad. No se puede reemplazar la segunda versión de esta función. Lo llama el C++ SDK de Build Insights cuando un analizador forma parte de un grupo de reregistradores. Todas las llamadas a la versión 2 se redirigen a la versión 1.

### <a name="version-1"></a>versión 1

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>Versión 2

```cpp
AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Parámetros

\ *eventStack*
Pila de eventos para este evento de detención de actividad. Para obtener más información sobre las pilas de eventos, vea [eventos](../event-table.md).

\ *relogSession*
Este parámetro no se utiliza.

### <a name="return-value"></a>Valor devuelto

Código de [AnalysisControl](analysis-control-enum-class.md) que describe lo que debería pasar a continuación.

::: moniker-end
