---
title: Estructura de ANALYSIS_DESCRIPTOR
description: El C++ SDK de Build insights ANALYSIS_DESCRIPTOR referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fc11ce11e1faaae02edb36aac447c18ea8107e35
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334107"
---
# <a name="analysis_descriptor-structure"></a>Estructura de ANALYSIS_DESCRIPTOR

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura `ANALYSIS_DESCRIPTOR` se usa con las funciones [analyzea](../functions/analyze-a.md) y [AnalyzeW](../functions/analyze-w.md) . Describe cómo se debe analizar un seguimiento de seguimiento de eventos para Windows (ETW).

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct ANALYSIS_DESCRIPTOR_TAG
{
    unsigned                NumberOfPasses;
    ANALYSIS_CALLBACKS      Callbacks;
    void*                   Context;
} ANALYSIS_DESCRIPTOR;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `NumberOfPasses` | El número de pasos de análisis que se deben realizar en el seguimiento de ETW. |
| `Callbacks` | Objeto [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) que especifica las funciones a las que se va a llamar durante la sesión de análisis. |
| `Context` | Contexto proporcionado por el usuario que se pasa como argumento a todas las funciones de devolución de llamada especificadas en `Callbacks` |

## <a name="remarks"></a>Comentarios

La estructura de `Callbacks` solo acepta punteros a funciones no miembro. Puede evitar esta limitación si establece `Context` en un puntero de objeto. Este puntero de objeto se pasará como argumento a todas las funciones de devolución de llamada que no son miembros. Utilice este puntero para llamar a funciones miembro desde dentro de las funciones de devolución de llamada que no son miembros.

::: moniker-end
