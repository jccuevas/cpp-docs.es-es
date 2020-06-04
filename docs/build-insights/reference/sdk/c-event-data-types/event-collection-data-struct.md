---
title: estructura EVENT_COLLECTION_DATA
description: El SDK de C++ Build Insights EVENT_COLLECTION_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 88ba39ede8c86f47c2e6458332ae005eddc06fda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325694"
---
# <a name="event_collection_data-structure"></a>estructura EVENT_COLLECTION_DATA

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `EVENT_COLLECTION_DATA` estructura describe una matriz de [elementos EVENT_DATA.](event-data-struct.md)

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct EVENT_COLLECTION_DATA_TAG
{
    unsigned int            Count;
    const EVENT_DATA*       Elements;

} EVENT_COLLECTION_DATA;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `Count` | El número `EVENT_DATA` de elementos de la matriz. |
| `Elements` | Puntero al `EVENT_DATA` primer elemento de la matriz. |

::: moniker-end
