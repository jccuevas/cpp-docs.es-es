---
title: Relog
description: Referencia de la función Relog del SDK de C+++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28b290d2bf2880ce2f534fa1cd91750890e2fead
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323777"
---
# <a name="relog"></a>Relog

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `Relog` función se utiliza para leer eventos MSVC de un seguimiento de seguimiento de eventos para Windows (ETW) y escribirlos en un nuevo seguimiento ETW modificado.

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

*TAnalyzerGroupMembers*\
Este parámetro siempre se deduce.

*TReloggerGroupMembers*\
Este parámetro siempre se deduce.

*inputLogFile*\
El seguimiento ETW de entrada desde el que desea leer eventos.

*outputLogFile*\
El archivo en el que se escribiron los nuevos eventos.

*numberOfAnalysisPasses*\
El número de pasos de análisis pasa para ejecutarse en el seguimiento de entrada. El seguimiento pasa a través del grupo de analizador proporcionado una vez por paso de análisis.

*systemEventsRetentionFlags*\
Una máscara de bits que especifica qué eventos ETW del sistema se deben mantener en el seguimiento reiniciado. Para obtener más información, consulte [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md).

*analyzerGroup*\
El grupo de analizadores utilizado para la fase de análisis de la sesión de recorrección. Llame a [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) para crear un grupo de analizadores. Para utilizar un grupo de analizador dinámico obtenido de [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), primero `MakeStaticAnalyzerGroup`encapsularlo dentro de un grupo de analizador estático pasando su dirección a .

*reloggerGroup*\
El grupo de reregistrador que vuelve a registrar eventos en el archivo de seguimiento especificado en *outputLogFile*. Llame a [MakeStaticReloggerGroup](make-static-relogger-group.md) para crear un grupo de reregistradores. Para utilizar un grupo de reregistrador dinámico obtenido de [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md), primero encapsularlo dentro de un grupo de registrador estático pasando su dirección a `MakeStaticReloggerGroup`.

### <a name="return-value"></a>Valor devuelto

Un código de resultado de la [enumeración de RESULT_CODE.](../other-types/result-code-enum.md)

### <a name="remark"></a>Comentario

El seguimiento de entrada se pasa a través del grupo de *analizadornumberOfAnalysisPasses* times. No hay una opción similar para volver a registrar pases. La traza se pasa a través del grupo del registrador una sola vez, después de que se completen todas las pasadas de análisis.

No se admite el reregistro de eventos del sistema como muestras de CPU desde una clase de relogger. Utilice el parámetro *systemEventsRetentionFlags* para decidir qué eventos del sistema se mantendrán en el seguimiento de salida.

::: moniker-end
