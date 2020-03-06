---
title: Estructura de EVENT_COLLECTION_DATA
description: El C++ SDK de Build insights EVENT_COLLECTION_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1a622a8459b6aa6d9dcbe0faaf90ae545b449466
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335247"
---
# <a name="event_collection_data-structure"></a>Estructura de EVENT_COLLECTION_DATA

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura `EVENT_COLLECTION_DATA` describe una matriz de elementos [EVENT_DATA](event-data-struct.md) .

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
| `Count` | Número de elementos `EVENT_DATA` de la matriz. |
| `Elements` | Puntero al primer `EVENT_DATA` elemento de la matriz. |

::: moniker-end
