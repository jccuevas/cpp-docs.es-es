---
title: TRANSLATION_UNIT_PASS_CODE enum
description: El SDK de C++ Build Insights TRANSLATION_UNIT_PASS_CODE referencia de enumeración.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRANSLATION_UNIT_PASS_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b0162d7e53bb7ee7035b94a6b640f6db87cd8b8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325284"
---
# <a name="translation_unit_pass_code-enum"></a>TRANSLATION_UNIT_PASS_CODE enum

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `TRANSLATION_UNIT_PASS_CODE` enumeración.

## <a name="members"></a>Miembros

| Nombre | Value | Descripción |
|--|--|--|
| `TRANSLATION_UNIT_PASS_CODE_FRONT_END` | 0 (0x00000000) | El paso de front-end, responsable de analizar el código fuente y convertirlo en lenguaje intermedio. |
| `TRANSLATION_UNIT_PASS_CODE_BACK_END` | 1 (0x00000001) | El pase back-end, responsable de optimizar el lenguaje intermedio y convertirlo en código de máquina. |

## <a name="remarks"></a>Observaciones

Utilizado por las funciones del SDK de C.

::: moniker-end
