---
title: Estructura de TEMPLATE_INSTANTIATION_DATA
description: El C++ SDK de Build insights TEMPLATE_INSTANTIATION_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9aa669d715dbe56ce7e889330f46f307f520710f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335085"
---
# <a name="template_instantiation_data-structure"></a>Estructura de TEMPLATE_INSTANTIATION_DATA

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura `TEMPLATE_INSTANTIATION_DATA` describe una creación de instancias de plantilla.

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
| `SpecializationSymbolKey` | Clave para el tipo de especialización de la plantilla. Este valor es único en el seguimiento que se está analizando. |
| `PrimaryTemplateSymbolKey` | Clave para el tipo de plantilla principal que se ha especializado. Este valor es único en el seguimiento que se está analizando. |
| `KindCode` | Tipo de la creación de instancias de la plantilla. Para obtener más información, vea [TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md). |

## <a name="remarks"></a>Comentarios

Las claves de la estructura `TEMPLATE_INSTANTIATION_DATA` son únicas dentro del seguimiento que se está analizando. Sin embargo, dos claves diferentes que provienen de diferentes fases de front-end del compilador pueden apuntar a dos tipos idénticos. Al consumir `TEMPLATE_INSTANTIATION_DATA` información de varias fases de front-end del compilador, utilice los eventos [SYMBOL_NAME](../event-table.md#symbol-name) para determinar si dos tipos son iguales. `SymbolName` eventos se emiten al final de una fase de front-end del compilador, después de que se hayan realizado todas las creaciones de instancias de la plantilla.

::: moniker-end
