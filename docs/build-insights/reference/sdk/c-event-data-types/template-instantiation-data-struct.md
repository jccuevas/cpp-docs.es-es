---
title: estructura TEMPLATE_INSTANTIATION_DATA
description: El SDK de C++ Build Insights TEMPLATE_INSTANTIATION_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a38d19368e7c0a9912907f1da6e7a2e31ffe8d90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325327"
---
# <a name="template_instantiation_data-structure"></a>estructura TEMPLATE_INSTANTIATION_DATA

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `TEMPLATE_INSTANTIATION_DATA` estructura describe una creación de instancias de plantilla.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct TEMPLATE_INSTANTIATION_DATA_TAG
{
    unsigned long long  SpecializationSymbolKey;
    unsigned long long  PrimaryTemplateSymbolKey;
    int                 KindCode;

} TEMPLATE_INSTANTIATION_DATA;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `SpecializationSymbolKey` | La clave para el tipo de especialización de plantilla. Este valor es único dentro del seguimiento que se está analizando. |
| `PrimaryTemplateSymbolKey` | La clave para el tipo de plantilla principal que estaba especializado. Este valor es único dentro del seguimiento que se está analizando. |
| `KindCode` | Tipo de creación de instancias de plantilla. Para obtener más información, consulte [TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md). |

## <a name="remarks"></a>Observaciones

Las claves `TEMPLATE_INSTANTIATION_DATA` de la estructura son únicas dentro del seguimiento que se está analizando. Sin embargo, dos claves diferentes procedentes de pases de front-end del compilador diferentes pueden apuntar a dos tipos idénticos. Al `TEMPLATE_INSTANTIATION_DATA` consumir información de varias pasadas de front-end del compilador, use los eventos [SYMBOL_NAME](../event-table.md#symbol-name) para determinar si dos tipos son iguales. `SymbolName`los eventos se emiten al final de un paso de front-end del compilador, después de que se hayan realizado todas las instancias de plantilla.

::: moniker-end
