---
title: OnBeginEndPassFunc (typedef)
description: La C++ referencia de definición de tipo ONBEGINENDPASSFUNC del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnBeginEndPassFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6f5e602fdc460acf8e53307e88a1a3d7ad000893
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334059"
---
# <a name="onbeginendpassfunc-typedef"></a>OnBeginEndPassFunc (typedef)

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

El `OnBeginEndPassFunc` typedef es una de las firmas de función usadas en las estructuras [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) y [RELOG_CALLBACKS](relog-callbacks-struct.md) .

## <a name="syntax"></a>Sintaxis

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnBeginEndPassFunc)(
    void*                           callbackContext);
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `callbackContext` |  |

::: moniker-end
