---
title: CALLBACK_CODE enum
description: El SDK de C++ Build Insights CALLBACK_CODE referencia enum.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d0d3dcc70040f562cd40755188e545f709a807b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329193"
---
# <a name="callback_code-enum"></a>CALLBACK_CODE enum

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `CALLBACK_CODE` enumeración se utiliza para controlar el flujo de una sesión de análisis o relogging. Devuelve un valor CALLBACK_CODE de las funciones [de ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) o [RELOG_CALLBACKS](relog-callbacks-struct.md) para controlar lo que debe suceder a continuación.

## <a name="members"></a>Miembros

| Nombre | Value | Descripción |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | Continúe la sesión actual de análisis o recorrección normalmente. |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x00000002) | Cancele la sesión de análisis o recorrección actual y señale un error. |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x00000004) | Cancele el análisis actual o la sesión de reregistro. |

::: moniker-end
