---
title: Analizar
description: La referencia de la función Analizar del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 08b3643270cc785b3fbea36720d192b4a1473104
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324108"
---
# <a name="analyze"></a>Analizar

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `Analyze` función se utiliza para analizar un seguimiento de seguimiento de eventos para Windows (ETW) obtenido de MSVC mientras se realiza el seguimiento de una compilación de C++. Los eventos del seguimiento ETW se reenvían secuencialmente a un grupo de analizadores proporcionado por el autor de la llamada. Esta función admite análisis de varias pasadas que permiten reenviar la secuencia de eventos al grupo de analizadores varias veces seguidas.

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

*TAnalyzerGroupMembers*\
Este parámetro siempre se deduce.

*inputLogFile*\
El seguimiento ETW de entrada desde el que desea leer eventos.

*numberOfPasses*\
El número de pasos de análisis pasa para ejecutarse en el seguimiento de entrada. El seguimiento pasa a través del grupo de analizador proporcionado una vez por paso de análisis.

*analyzerGroup*\
El grupo de analizadores utilizado para el análisis. Llame a [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) para crear un grupo de analizadores. Para utilizar un grupo de analizador dinámico obtenido de [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), primero `MakeStaticAnalyzerGroup`encapsularlo dentro de un grupo de analizador estático pasando su dirección a .

### <a name="return-value"></a>Valor devuelto

Un código de resultado de la [enumeración de RESULT_CODE.](../other-types/result-code-enum.md)

::: moniker-end
