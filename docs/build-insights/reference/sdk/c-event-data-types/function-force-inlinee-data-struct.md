---
title: Estructura de FUNCTION_FORCE_INLINEE_DATA
description: El C++ SDK de Build insights FUNCTION_FORCE_INLINEE_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_FORCE_INLINEE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3d6929f2f16e9b1bd79b7fb8b383b40e031268bf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335151"
---
# <a name="function_force_inlinee_data-structure"></a>Estructura de FUNCTION_FORCE_INLINEE_DATA

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura `FUNCTION_FORCE_INLINEE_DATA` describe una función insertada en el forzado.

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
