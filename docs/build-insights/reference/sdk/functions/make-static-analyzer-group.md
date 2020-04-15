---
title: MakeStaticAnalyzerGroup
description: Referencia de la función MakeStaticAnalyzerGroup del SDK de Compilación de C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 72f7f5d7a408436902394451a52dd66efe1d93f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323941"
---
# <a name="makestaticanalyzergroup"></a>MakeStaticAnalyzerGroup

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `MakeStaticAnalyzerGroup` función se utiliza para crear un grupo de analizadores estáticos que se puede pasar a funciones como [Analizar](analyze.md) o [Relog](relog.md). Los miembros de un grupo de analizadores reciben eventos uno por uno de izquierda a derecha, hasta que se analizan todos los eventos de un seguimiento.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>Parámetros

*TAnalyzerPtrs*\
Este parámetro siempre se deduce.

*Analizadores*\
Un paquete de parámetros de punteros [IAnalyzer](../other-types/ianalyzer-class.md) incluidos en el grupo de analizadores estáticos. Estos punteros pueden `std::unique_ptr`ser `std::shared_ptr`sin procesar, , o .

### <a name="return-value"></a>Valor devuelto

Un grupo de analizadores estáticos. Utilice la palabra clave **auto** para capturar el valor devuelto.

## <a name="remarks"></a>Observaciones

A diferencia de los grupos de analizadordinámicos dinámicos, los miembros de un grupo de analizador estático deben conocerse en tiempo de compilación. Además, un grupo de analizador estático contiene punteros [IAnalyzer](../other-types/ianalyzer-class.md) que no tienen un comportamiento polimórfico. Cuando se utiliza un grupo de analizador estático para analizar un `IAnalyzer` seguimiento de seguimiento de eventos para Windows (ETW), las llamadas a la interfaz siempre se resuelven en el objeto al que apunta directamente el miembro del grupo de analizadores. Esta pérdida de flexibilidad viene con la posibilidad de tiempos de procesamiento de eventos más rápidos. Si los miembros de un grupo de analizadores no se pueden conocer `IAnalyzer` en tiempo de compilación, o si necesita un comportamiento polimórfico en los punteros, considere la posibilidad de usar un grupo de analizador dinámico. Para usar un grupo de analizador dinámico, llame a [MakeDynamicAnalyzerGroup](make-static-analyzer-group.md) en su lugar.

::: moniker-end
