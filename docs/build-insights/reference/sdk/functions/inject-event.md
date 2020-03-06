---
title: InjectEvent
description: La C++ referencia de la función INJECTEVENT del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7b53eb71cf7a2ae40d04dbc3f8b5829f2737aba4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334419"
---
# <a name="injectevent"></a>InjectEvent

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Se llama a la función `InjectEvent` dentro de un registrador que implementa la interfaz [IRelogger](../other-types/irelogger-class.md) . Se usa para escribir un evento de seguimiento de eventos para Windows (ETW) en el archivo de seguimiento de salida de una sesión de registro.

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

\ *relogSession*
Puntero a la sesión que se va a registrar. Se proporciona una sesión de registro para los reregistradores que implementan la interfaz `IRelogger`. Para obtener más información, vea [IRelogger](../other-types/irelogger-class.md).

*providerId*\
Un GUID del proveedor de seguimiento de eventos para Windows (ETW) en el que se registra el evento ETW.

*eventDescriptor*\
Descriptor de eventos ETW para el evento ETW que se ha reiniciado.

*processId*\
Identificador de proceso (PID) del evento ETW que se vuelve a registrar.

\ *threadId*
Identificador del subproceso (TID) del evento ETW que se ha reiniciado.

\ *processorIndex*
Índice del procesador para el evento ETW que se ha reiniciado.

*marca* de tiempo\
Marca de tiempo del evento ETW que se ha reiniciado.

\ de *datos*
Un puntero a los datos que se deben incluir en el evento ETW que se ha reiniciado.

\ *byteCount*
Tamaño de los datos, en bytes, a los que apuntan los *datos*.

## <a name="remarks"></a>Comentarios

Para obtener más información sobre los conceptos de ETW, como el *GUID del proveedor* y el *descriptor de eventos*, consulte la documentación de [ETW](/windows/win32/etw/about-event-tracing). Para obtener más información sobre cómo iniciar una sesión de registro con C++ el SDK de Build Insights, consulte [relog](relog.md).

::: moniker-end
