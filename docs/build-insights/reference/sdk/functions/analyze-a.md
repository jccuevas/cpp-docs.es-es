---
title: AnalyzeA
description: Referencia de la función AnalyzeA del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalyzeA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7c7602c49ab5f3ce67693424019e253727563293
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324145"
---
# <a name="analyzea"></a>AnalyzeA

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `AnalyzeA` función se utiliza para analizar eventos MSVC leídos de un seguimiento de seguimiento de eventos para Windows (ETW) de entrada.

## <a name="syntax"></a>Sintaxis

```cpp
enum RESULT_CODE AnalyzeA(
    const char*                inputLogFile,
    const ANALYSIS_DESCRIPTOR* analysisDescriptor);
```

### <a name="parameters"></a>Parámetros

*inputLogFile*\
El seguimiento ETW de entrada desde el que desea leer eventos.

*analysisDescriptor*\
Puntero a un objeto [ANALYSIS_DESCRIPTOR.](../other-types/analysis-descriptor-struct.md) Utilice este objeto para configurar el análisis.

### <a name="return-value"></a>Valor devuelto

Un código de resultado de la [enumeración de RESULT_CODE.](../other-types/result-code-enum.md)

::: moniker-end
