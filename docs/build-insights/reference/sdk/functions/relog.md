---
title: Relog
description: La C++ referencia de la función relog del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1ce09101deebd957de4b9305762dc37f38b53f4e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334287"
---
# <a name="relog"></a>Relog

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `Relog` se usa para leer eventos MSVC desde un seguimiento de seguimiento de eventos para Windows (ETW) y escribirlos en un seguimiento ETW nuevo y modificado.

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const char*                                   inputLogFile,
    const char*                                   outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const wchar_t*                                inputLogFile,
    const wchar_t*                                outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>Parámetros

\ *TAnalyzerGroupMembers*
Este parámetro siempre se deduce.

\ *TReloggerGroupMembers*
Este parámetro siempre se deduce.

\ *inputLogFile*
Seguimiento de ETW de entrada del que desea leer eventos.

\ *outputLogFile*
Archivo en el que se van a escribir los nuevos eventos.

\ *numberOfAnalysisPasses*
El número de pasos de análisis que se ejecutarán en el seguimiento de entrada. El seguimiento se pasa a través del grupo de analizador proporcionado una vez por cada paso del análisis.

\ *systemEventsRetentionFlags*
Máscara de máscara que especifica qué eventos ETW del sistema mantener en el seguimiento que se ha reiniciado. Para obtener más información, vea [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md).

\ *analyzerGroup*
El grupo de analizador que se usa para la fase de análisis de la sesión de reregistro. Llame a [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) para crear un grupo de Analyzer. Para usar un grupo de analizador dinámico Obtenido de [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), primero debe encapsularlo dentro de un grupo de analizador estático pasando su dirección a `MakeStaticAnalyzerGroup`.

\ *reloggerGroup*
El grupo de reregistradores que vuelve a registrar los eventos en el archivo de seguimiento especificado en *outputLogFile*. Llame a [MakeStaticReloggerGroup](make-static-relogger-group.md) para crear un grupo de registro. Para usar un grupo de registradores dinámicos Obtenido de [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md), primero debe encapsularlo dentro de un grupo de registradores estáticos pasando su dirección a `MakeStaticReloggerGroup`.

### <a name="return-value"></a>Valor devuelto

Código de resultado de la enumeración [RESULT_CODE](../other-types/result-code-enum.md) .

### <a name="remark"></a>Comentario

El seguimiento de entrada se pasa a través del grupo de analizador *numberOfAnalysisPasses* veces. No hay ninguna opción similar para las fases de registro. El seguimiento se pasa con el grupo de reregistradores solo una vez, una vez completados todos los pasos del análisis.

No se admite el reregistro de eventos del sistema como ejemplos de CPU desde una clase de reregistrador. Use el parámetro *systemEventsRetentionFlags* para decidir qué eventos del sistema deben conservarse en el seguimiento de salida.

::: moniker-end
