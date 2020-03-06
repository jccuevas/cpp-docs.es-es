---
title: Analizar
description: Referencia C++ de la función de análisis del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 49161641d1cff1c64261d95bb2caace2f802543a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334437"
---
# <a name="analyze"></a>Analizar

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `Analyze` se usa para analizar un seguimiento de seguimiento de eventos para Windows (ETW) Obtenido de MSVC mientras C++ se realiza un seguimiento de una compilación. Los eventos del seguimiento de ETW se reenvían secuencialmente a un grupo de Analyzer proporcionado por el autor de la llamada. Esta función admite análisis de paso múltiple que permiten reenviar el flujo de eventos al grupo de analizador varias veces en una fila.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const char*                                   inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const wchar_t*                                inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>Parámetros

\ *TAnalyzerGroupMembers*
Este parámetro siempre se deduce.

\ *inputLogFile*
Seguimiento de ETW de entrada del que desea leer eventos.

\ *numberOfPasses*
El número de pasos de análisis que se ejecutarán en el seguimiento de entrada. El seguimiento se pasa a través del grupo de analizador proporcionado una vez por cada paso del análisis.

\ *analyzerGroup*
El grupo de analizador que se usa para el análisis. Llame a [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) para crear un grupo de Analyzer. Para usar un grupo de analizador dinámico Obtenido de [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), primero debe encapsularlo dentro de un grupo de analizador estático pasando su dirección a `MakeStaticAnalyzerGroup`.

### <a name="return-value"></a>Valor devuelto

Código de resultado de la enumeración [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
