---
title: Clase IRelogger
description: Referencia C++ de la clase IRELOGGER del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d0796cec3fe4ac6183279e8d8013a9550f18b61c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857064"
---
# <a name="irelogger-class"></a>Clase IRelogger

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `IRelogger` proporciona una interfaz para el registro de un seguimiento de seguimiento de eventos para Windows (ETW). Se usa con las funciones [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md) y [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) . Use `IRelogger` como una clase base para crear su propio registrador que puede formar parte de un grupo de registro de registro.

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

## <a name="remarks"></a>Comentarios

El valor devuelto predeterminado para todas las funciones que no se reemplazan es `AnalysisControl::CONTINUE`. Para obtener más información, vea [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Miembros

### <a name="destructor"></a>Destructor

[~ IRelogger](#irelogger-destructor)

### <a name="functions"></a>Funciones

\ [OnBeginRelogging](#on-begin-relogging)
\ [OnBeginReloggingPass](#on-begin-relogging-pass)
\ [OnEndRelogging](#on-end-relogging)
\ [OnEndReloggingPass](#on-end-relogging-pass)
\ [OnSimpleEvent](#on-simple-event)
\ [OnStartActivity](#on-start-activity)
\ [OnStopActivity](#on-stop-activity)
[OnTraceInfo](#on-trace-info)

## <a name="irelogger-destructor"></a>~ IRelogger

Destruye la clase IRelogger.

```cpp
virtual ~IRelogger();
```

## <a name="on-begin-relogging"></a>OnBeginRelogging

Se llama a esta función antes de que se inicie el paso de registro.

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>Valor devuelto

Código de [AnalysisControl](analysis-control-enum-class.md) que describe lo que debería pasar a continuación.

## <a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

Se llama a esta función al principio del paso de registro.

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>Valor devuelto

Código de [AnalysisControl](analysis-control-enum-class.md) que describe lo que debería pasar a continuación.

## <a name="on-end-relogging"></a>OnEndRelogging

Se llama a esta función una vez finalizada la fase de reregistro.

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>Valor devuelto

Código de [AnalysisControl](analysis-control-enum-class.md) que describe lo que debería pasar a continuación.

## <a name="on-end-relogging-pass"></a>OnEndReloggingPass

Esta función se llama al final del paso de registro.

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>Valor devuelto

Código de [AnalysisControl](analysis-control-enum-class.md) que describe lo que debería pasar a continuación.

## <a name="on-simple-event"></a>OnSimpleEvent

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

Se llama a esta función cuando se está procesando un evento simple.

### <a name="parameters"></a>Parámetros

\ *eventStack*
Pila de eventos para este evento simple. Para obtener más información sobre las pilas de eventos, vea [eventos](../event-table.md).

### <a name="return-value"></a>Valor devuelto

Código de [AnalysisControl](analysis-control-enum-class.md) que describe lo que debería pasar a continuación.

## <a name="on-start-activity"></a>OnStartActivity

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

Se llama a esta función cuando se está procesando un evento de inicio de actividad.

### <a name="parameters"></a>Parámetros

\ *eventStack*
Pila de eventos para este evento de inicio de actividad. Para obtener más información sobre las pilas de eventos, vea [eventos](../event-table.md).

### <a name="return-value"></a>Valor devuelto

Código de [AnalysisControl](analysis-control-enum-class.md) que describe lo que debería pasar a continuación.

## <a name="on-stop-activity"></a>OnStopActivity

Se llama a esta función cuando se está procesando un evento de detención de actividad.

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>Parámetros

\ *eventStack*
Pila de eventos para este evento de detención de actividad. Para obtener más información sobre las pilas de eventos, vea [eventos](../event-table.md).

### <a name="return-value"></a>Valor devuelto

Código de [AnalysisControl](analysis-control-enum-class.md) que describe lo que debería pasar a continuación.

## <a name="on-trace-info"></a>OnTraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

Esta función se llama una vez al principio de cada paso de análisis o de registro.

### <a name="parameters"></a>Parámetros

\ *traceInfo*
Un objeto [TraceInfo](../cpp-event-data-types/trace-info.md) que contiene propiedades útiles sobre el seguimiento que se está consumiendo.

### <a name="return-value"></a>Valor devuelto

Código de [AnalysisControl](analysis-control-enum-class.md) que describe lo que debería pasar a continuación.

::: moniker-end
