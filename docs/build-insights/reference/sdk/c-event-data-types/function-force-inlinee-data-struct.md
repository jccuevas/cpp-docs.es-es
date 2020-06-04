---
title: estructura FUNCTION_FORCE_INLINEE_DATA
description: El SDK de C++ Build Insights FUNCTION_FORCE_INLINEE_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_FORCE_INLINEE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a4781c9157130cb46e92906017af98710f5637b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325495"
---
# <a name="function_force_inlinee_data-structure"></a>estructura FUNCTION_FORCE_INLINEE_DATA

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `FUNCTION_FORCE_INLINEE_DATA` estructura describe una función de inlineación de fuerza.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct FUNCTION_FORCE_INLINEE_DATA_TAG
{
    const char*         Name;
    unsigned short      Size;

} FUNCTION_FORCE_INLINEE_DATA;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `Name` | Nombre de la función, codificado en UTF-8. |
| `Size` | Tamaño de la función, como una serie de instrucciones intermedias. |

::: moniker-end
