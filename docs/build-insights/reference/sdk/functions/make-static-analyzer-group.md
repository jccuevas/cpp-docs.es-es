---
title: MakeStaticAnalyzerGroup
description: La C++ referencia de la función MAKESTATICANALYZERGROUP del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5eabb0fcbb0a0bb0eea0f4e6bbf27b8e4c53c3ab
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334395"
---
# <a name="makestaticanalyzergroup"></a>MakeStaticAnalyzerGroup

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `MakeStaticAnalyzerGroup` se usa para crear un grupo de analizador estático que se puede pasar a funciones como [Analyze](analyze.md) o [relog](relog.md). Los miembros de un grupo de analizador reciben eventos uno por uno de izquierda a derecha, hasta que se analizan todos los eventos de un seguimiento.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>Parámetros

\ *TAnalyzerPtrs*
Este parámetro siempre se deduce.

*analizadores*\
Un paquete de parámetros de punteros [IAnalyzer](../other-types/ianalyzer-class.md) incluido en el grupo de analizador estático. Estos punteros pueden ser RAW, `std::unique_ptr`o `std::shared_ptr`.

### <a name="return-value"></a>Valor devuelto

Un grupo de analizador estático. Use la palabra clave **auto** para capturar el valor devuelto.

## <a name="remarks"></a>Comentarios

A diferencia de los grupos de analizador dinámico, los miembros de un grupo de analizador estático deben conocerse en tiempo de compilación. Además, un grupo de analizador estático contiene punteros [IAnalyzer](../other-types/ianalyzer-class.md) que no tienen un comportamiento polimórfico. Cuando se usa un grupo de analizador estático para analizar un seguimiento de seguimiento de eventos para Windows (ETW), las llamadas a la interfaz `IAnalyzer` siempre se resuelven en el objeto al que apunta directamente el miembro del grupo Analyzer. Esta pérdida de flexibilidad viene con la posibilidad de tiempos de procesamiento de eventos más rápidos. Si los miembros de un grupo de analizador no se pueden conocer en tiempo de compilación, o si necesita un comportamiento polimórfico en los punteros de `IAnalyzer`, considere la posibilidad de usar un grupo de analizador dinámico. Para usar un grupo de analizador dinámico, llame a [MakeDynamicAnalyzerGroup](make-static-analyzer-group.md) en su lugar.

::: moniker-end
