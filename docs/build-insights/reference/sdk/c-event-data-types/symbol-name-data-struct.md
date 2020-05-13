---
title: estructura SYMBOL_NAME_DATA
description: El SDK de C++ Build Insights SYMBOL_NAME_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1217572f20a772fde629533d6ab170c14dc5b5e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325336"
---
# <a name="symbol_name_data-structure"></a>estructura SYMBOL_NAME_DATA

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `SYMBOL_NAME_DATA` estructura describe un símbolo de front-end del compilador.

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
| `Key` | La llave del símbolo. Este valor es único dentro del seguimiento que se está analizando. |
| `Name` | El nombre del símbolo. |

## <a name="remarks"></a>Observaciones

Los símbolos procedentes de dos pasadas de front-end del compilador diferentes pueden tener el mismo nombre pero una clave diferente. En este caso, utilice nombres de símbolo para determinar si dos tipos son iguales.

::: moniker-end
