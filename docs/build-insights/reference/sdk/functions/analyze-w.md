---
title: AnalyzeW
description: La C++ referencia de la función ANALYZEW del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalyzeW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bd9b401f08941134d3c267df5c23c5d9e981cb86
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334491"
---
# <a name="analyzew"></a>AnalyzeW

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `AnalyzeW` se usa para analizar eventos MSVC leídos de un seguimiento de seguimiento de eventos de entrada para Windows (ETW).

## <a name="syntax"></a>Sintaxis

```cpp
enum RESULT_CODE AnalyzeW(
    const wchar_t*             inputLogFile,
    const ANALYSIS_DESCRIPTOR* analysisDescriptor);
```

### <a name="parameters"></a>Parámetros

\ *inputLogFile*
Seguimiento de ETW de entrada del que desea leer eventos.

\ *analysisDescriptor*
Puntero a un objeto [ANALYSIS_DESCRIPTOR](../other-types/analysis-descriptor-struct.md) . Utilice este objeto para configurar el análisis.

### <a name="return-value"></a>Valor devuelto

Código de resultado de la enumeración [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
