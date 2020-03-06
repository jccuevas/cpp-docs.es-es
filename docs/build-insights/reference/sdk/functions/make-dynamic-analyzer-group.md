---
title: MakeDynamicAnalyzerGroup
description: La C++ referencia de la función MAKEDYNAMICANALYZERGROUP del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f409d685c6af6514b73cd837d668a962c1a0d01a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334407"
---
# <a name="makedynamicanalyzergroup"></a>MakeDynamicAnalyzerGroup

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `MakeDynamicAnalyzerGroup` se usa para crear un grupo de analizador dinámico. Los miembros de un grupo de analizador reciben eventos uno por uno de izquierda a derecha, hasta que se analizan todos los eventos de un seguimiento.

## <a name="syntax"></a>Sintaxis

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>Parámetros

*analizadores*\
Vector de punteros [IAnalyzer](../other-types/ianalyzer-class.md) incluido en el grupo de analizador dinámico. Estos punteros pueden ser RAW, `std::unique_ptr`o `std::shared_ptr`.

### <a name="return-value"></a>Valor devuelto

Un grupo de analizador dinámico. Use la palabra clave **auto** para capturar el valor devuelto.

## <a name="remarks"></a>Comentarios

A diferencia de los grupos de analizador estático, los miembros de un grupo de analizador dinámico no necesitan conocerse en tiempo de compilación. Puede elegir los miembros del grupo del analizador en tiempo de ejecución en función de la entrada del programa o en función de otros valores desconocidos en tiempo de compilación. A diferencia de los grupos de analizador estático, los punteros [IAnalyzer](../other-types/ianalyzer-class.md) dentro de un grupo de analizador dinámico tienen un comportamiento polimórfico y las llamadas a funciones virtuales se envían correctamente. Esta flexibilidad se produce a costa de un tiempo de procesamiento de eventos posiblemente más lento. Cuando todos los miembros del grupo del analizador se conocen en tiempo de compilación, y si no necesita un comportamiento polimórfico, considere la posibilidad de usar un grupo de analizador estático. Para usar un grupo de analizador estático, llame a [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) en su lugar.

Un grupo de analizador dinámico se puede encapsular dentro de un grupo de analizador estático. Se realiza pasando su dirección a [MakeStaticAnalyzerGroup](make-static-analyzer-group.md). Utilice esta técnica para pasar grupos de analizador dinámico a funciones como [Analyze](analyze.md), que solo aceptan grupos de analizador estático.

::: moniker-end
