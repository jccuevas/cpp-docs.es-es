---
title: estructura INVOCATION_VERSION_DATA
description: El SDK de C++ Build Insights INVOCATION_VERSION_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1211b4eb999fd63767af71c6884d7d20d6920df0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325471"
---
# <a name="invocation_version_data-structure"></a>estructura INVOCATION_VERSION_DATA

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `INVOCATION_VERSION_DATA` estructura describe un número de versión como un grupo de valores integrales.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct INVOCATION_VERSION_DATA_TAG
{
    unsigned short VersionMajor;
    unsigned short VersionMinor;
    unsigned short BuildNumberMajor;
    unsigned short BuildNumberMinor;

} INVOCATION_VERSION_DATA;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `VersionMajor` | El número principal de la versión. |
| `VersionMinor` | El número menor de la versión. |
| `BuildNumberMajor` | El número mayor de la compilación. |
| `BuildNumberMinor` | Número menor de la compilación. |

::: moniker-end
