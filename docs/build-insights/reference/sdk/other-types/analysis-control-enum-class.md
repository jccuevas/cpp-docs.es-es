---
title: AnalysisControl (clase de enumeración)
description: La C++ referencia de enumeración ANALYSISCONTROL del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: cf162c11e0a7109b8d733dab79df80782398e14d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334125"
---
# <a name="analysiscontrol-enum-class"></a>AnalysisControl (clase de enumeración)

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase de enumeración `AnalysisControl` se utiliza para controlar el flujo de una sesión de análisis o de registro. Devuelve un código `AnalysisControl` de una función miembro [IAnalyzer](ianalyzer-class.md) o [IRelogger](irelogger-class.md) para controlar lo que debe ocurrir a continuación.

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `BLOCK` | Evita que el evento actual se propague más en el grupo de analizador o de reregistrador. |
| `CANCEL` | Cancela la sesión de análisis o de registro actual. |
| `CONTINUE` | Continuar el análisis actual o la sesión de registro con normalidad. Propagar el evento actual al siguiente miembro del grupo de analizador o de reregistrador. |
| `FAILURE` | Cancele el análisis actual o la sesión de registro y señale un error. |

::: moniker-end
