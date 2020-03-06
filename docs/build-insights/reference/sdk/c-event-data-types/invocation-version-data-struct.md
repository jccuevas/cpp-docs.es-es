---
title: Estructura de INVOCATION_VERSION_DATA
description: El C++ SDK de Build insights INVOCATION_VERSION_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 040b0f90b14133ec2b25f7a12d35b88d382c4f7a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335133"
---
# <a name="invocation_version_data-structure"></a>Estructura de INVOCATION_VERSION_DATA

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura `INVOCATION_VERSION_DATA` describe un número de versión como un grupo de valores enteros.

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
| `VersionMajor` | Número principal de la versión. |
| `VersionMinor` | Número secundario de la versión. |
| `BuildNumberMajor` | Número principal de la compilación. |
| `BuildNumberMinor` | Número secundario de la compilación. |

::: moniker-end
