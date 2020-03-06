---
title: Enumeración CALLBACK_CODE
description: El C++ SDK de Build insights CALLBACK_CODE referencia de enumeración.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 68eaa9aa04d2f0a55ac12fb7dde14a080188a38d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334095"
---
# <a name="callback_code-enum"></a>Enumeración CALLBACK_CODE

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La enumeración `CALLBACK_CODE` se utiliza para controlar el flujo de una sesión de análisis o de registro. Devuelve un valor CALLBACK_CODE de las funciones de [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) o [RELOG_CALLBACKS](relog-callbacks-struct.md) para controlar lo que debe ocurrir a continuación.

## <a name="members"></a>Miembros

| Name | Valor | Descripción |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | Continuar el análisis actual o la sesión de registro con normalidad. |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x00000002) | Cancele el análisis actual o la sesión de registro y señale un error. |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x00000004) | Cancela la sesión de análisis o de registro actual. |

::: moniker-end
