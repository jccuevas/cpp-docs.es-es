---
title: Estructura de SYMBOL_NAME_DATA
description: El C++ SDK de Build insights SYMBOL_NAME_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 618e84f198c20aa089dc7e06e1e6c09b96b6d273
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335097"
---
# <a name="symbol_name_data-structure"></a>Estructura de SYMBOL_NAME_DATA

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura `SYMBOL_NAME_DATA` describe un símbolo de front-end del compilador.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct SYMBOL_NAME_DATA_TAG
{
    unsigned long long  Key;
    const char*         Name;

} SYMBOL_NAME_DATA;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `Key` | La clave del símbolo. Este valor es único en el seguimiento que se está analizando. |
| `Name` | Nombre del símbolo. |

## <a name="remarks"></a>Comentarios

Los símbolos procedentes de dos pasos de front-end de compilador diferentes pueden tener el mismo nombre pero una clave diferente. En este caso, use nombres de símbolo para determinar si dos tipos son iguales.

::: moniker-end
