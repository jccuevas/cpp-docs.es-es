---
title: InjectEvent
description: Referencia de la función InjectEvent del SDK de C+++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c82aad5923eff60e5c72ceccaa39aa136f942665
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324037"
---
# <a name="injectevent"></a>InjectEvent

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `InjectEvent` función se llama dentro de un relogger que implementa la interfaz [IRelogger.](../other-types/irelogger-class.md) Se utiliza para escribir un evento de seguimiento de eventos para Windows (ETW) en el archivo de seguimiento de salida de una sesión de reregistro.

## <a name="syntax"></a>Sintaxis

```cpp
void InjectEvent(
    const void* relogSession,
    LPCGUID providerId,
    PCEVENT_DESCRIPTOR eventDescriptor,
    unsigned long processId,
    unsigned long threadId,
    unsigned short processorIndex,
    long long timestamp,
    unsigned char* data,
    unsigned long byteCount);
```

### <a name="parameters"></a>Parámetros

*relogSession*\
Un puntero a la sesión de recorrección. Se proporciona una sesión de relogging `IRelogger` a los reloggers que implementan la interfaz. Para obtener más información, consulte [IRelogger](../other-types/irelogger-class.md).

*providerId*\
Guid del proveedor de seguimiento de eventos para Windows (ETW) en el que se vuelve a registrar el evento ETW.

*eventDescriptor*\
El descriptor de eventos ETW para el evento ETW que se ha vuelto a registrar.

*processId*\
Identificador de proceso (PID) para el evento ETW que se ha vuelto a registrar.

*threadId*\
Identificador de subproceso (TID) para el evento ETW que se vuelve a registrar.

*processorIndex*\
El índice del procesador para el evento ETW que se ha vuelto a registrar.

*Timestamp*\
La marca de tiempo para el evento ETW que se vuelve a registrar.

*Datos*\
Puntero a los datos que se deben incluir en el evento ETW reregistrado.

*byteCount*\
El tamaño de los datos, en bytes, al que apuntan los *datos*.

## <a name="remarks"></a>Observaciones

Para obtener más información sobre los conceptos ETW, como *EL GUID del proveedor* y el descriptor de *eventos,* consulte la documentación de [ETW](/windows/win32/etw/about-event-tracing). Para obtener más información sobre cómo iniciar una sesión de reregistro con el SDK de C++ Build Insights, consulte [Relog](relog.md).

::: moniker-end
