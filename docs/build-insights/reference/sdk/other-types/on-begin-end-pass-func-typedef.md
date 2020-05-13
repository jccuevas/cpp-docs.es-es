---
title: OnBeginEndPassFunc typedef
description: La referencia de tipodef OnBeginEndPassFunc del SDK de Compilación de C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnBeginEndPassFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3b3fc453245a47463c29ceeb30dfdc48c79aef35
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329083"
---
# <a name="onbeginendpassfunc-typedef"></a>OnBeginEndPassFunc typedef

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `OnBeginEndPassFunc` definición de tipo es una de las firmas de función utilizadas en las estructuras [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) y [RELOG_CALLBACKS.](relog-callbacks-struct.md)

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
