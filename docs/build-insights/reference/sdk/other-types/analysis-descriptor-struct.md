---
title: estructura ANALYSIS_DESCRIPTOR
description: El SDK de C++ Build Insights ANALYSIS_DESCRIPTOR referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1de7f2a5bc3f02a327daaecf8c2cebc44687ba43
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323611"
---
# <a name="analysis_descriptor-structure"></a>estructura ANALYSIS_DESCRIPTOR

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `ANALYSIS_DESCRIPTOR` estructura se utiliza con las funciones [AnalyzeA](../functions/analyze-a.md) y [AnalyzeW.](../functions/analyze-w.md) Describe cómo se debe analizar un seguimiento de seguimiento de eventos para Windows (ETW).

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
| `NumberOfPasses` | El número de pasadas de análisis que se deben realizar sobre el seguimiento ETW. |
| `Callbacks` | Objeto [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) que especifica las funciones que se deben llamar durante la sesión de análisis. |
| `Context` | Un contexto proporcionado por el usuario que se pasa como argumento a todas las funciones de devolución de llamada especificadas en`Callbacks` |

## <a name="remarks"></a>Observaciones

La `Callbacks` estructura solo acepta punteros a funciones que no son miembros. Puede evitar esta limitación `Context` estableciendo en un puntero de objeto. Este puntero de objeto se pasará como argumento a todas las funciones de devolución de llamada que no sean miembros. Utilice este puntero para llamar a funciones miembro desde dentro de las funciones de devolución de llamada que no son miembros.

::: moniker-end
