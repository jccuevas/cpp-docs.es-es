---
title: AnalysisControl clase enum
description: La referencia de enumeración AnalysisControl del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e9431f878390127f2cefbe8f0ee42ca509e147de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323641"
---
# <a name="analysiscontrol-enum-class"></a>AnalysisControl clase enum

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `AnalysisControl` clase enum se utiliza para controlar el flujo de una sesión de análisis o relogging. Devuelve `AnalysisControl` un código de una función miembro [IAnalyzer](ianalyzer-class.md) o [IRelogger](irelogger-class.md) para controlar lo que debe suceder a continuación.

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `BLOCK` | Impide que el evento actual se propague más en el analizador o grupo de reregistradores. |
| `CANCEL` | Cancele el análisis actual o la sesión de reregistro. |
| `CONTINUE` | Continúe la sesión actual de análisis o recorrección normalmente. Propague el evento actual al siguiente analizador o miembro del grupo de registrador. |
| `FAILURE` | Cancele la sesión de análisis o recorrección actual y señale un error. |

::: moniker-end
