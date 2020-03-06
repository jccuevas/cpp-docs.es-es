---
title: Enumeración TRANSLATION_UNIT_PASS_CODE
description: El C++ SDK de Build insights TRANSLATION_UNIT_PASS_CODE referencia de enumeración.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRANSLATION_UNIT_PASS_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1219eed98fd01e8c91d8750977e2d8ca4498d649
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335049"
---
# <a name="translation_unit_pass_code-enum"></a>Enumeración TRANSLATION_UNIT_PASS_CODE

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Enumeración `TRANSLATION_UNIT_PASS_CODE`.

## <a name="members"></a>Miembros

| Name | Valor | Descripción |
|--|--|--|
| `TRANSLATION_UNIT_PASS_CODE_FRONT_END` | 0 (0x00000000) | La fase de front-end, responsable de analizar el código fuente y convertirlo en lenguaje intermedio. |
| `TRANSLATION_UNIT_PASS_CODE_BACK_END` | 1 (0x00000001) | La fase de back-end, responsable de optimizar el lenguaje intermedio y convertirlo en código máquina. |

## <a name="remarks"></a>Comentarios

Lo usan las funciones del SDK de C.

::: moniker-end
