---
title: MakeDynamicAnalyzerGroup
description: Referencia de la función MakeDynamicAnalyzerGroup del SDK de Compilación de C++ .
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 148eeea41f29ac6dd75653feed7f3f3f8c301911
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323958"
---
# <a name="makedynamicanalyzergroup"></a>MakeDynamicAnalyzerGroup

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `MakeDynamicAnalyzerGroup` función se utiliza para crear un grupo de analizadores dinámicos. Los miembros de un grupo de analizadores reciben eventos uno por uno de izquierda a derecha, hasta que se analizan todos los eventos de un seguimiento.

## <a name="syntax"></a>Sintaxis

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>Parámetros

*Analizadores*\
Vector de punteros [IAnalyzer](../other-types/ianalyzer-class.md) incluidos en el grupo de analizadores dinámicos. Estos punteros pueden `std::unique_ptr`ser `std::shared_ptr`sin procesar, , o .

### <a name="return-value"></a>Valor devuelto

Un grupo de analizadores dinámicos. Utilice la palabra clave **auto** para capturar el valor devuelto.

## <a name="remarks"></a>Observaciones

A diferencia de los grupos de analizadores estáticos, no es necesario conocer los miembros de un grupo de analizadores dinámicos en tiempo de compilación. Puede elegir los miembros del grupo del analizador en tiempo de ejecución en función de la entrada del programa o en función de otros valores desconocidos en tiempo de compilación. A diferencia de los grupos de analizadorestáticos, los punteros [IAnalyzer](../other-types/ianalyzer-class.md) dentro de un grupo de analizador dinámico tienen un comportamiento polimórfico y las llamadas a funciones virtuales se distribuyen correctamente. Esta flexibilidad se obtiene a costa de un tiempo de procesamiento de eventos posiblemente más lento. Cuando todos los miembros del grupo de analizadores se conocen en tiempo de compilación y si no necesita un comportamiento polimórfico, considere la posibilidad de usar un grupo de analizador estático. Para usar un grupo de analizador estático, llame a [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) en su lugar.

Un grupo de analizadores dinámicos se puede encapsular dentro de un grupo de analizadores estáticos. Se realiza pasando su dirección a [MakeStaticAnalyzerGroup](make-static-analyzer-group.md). Utilice esta técnica para pasar grupos de analizador dinámicos a funciones como [Analizar](analyze.md), que solo aceptan grupos de analizadorestáticos.

::: moniker-end
