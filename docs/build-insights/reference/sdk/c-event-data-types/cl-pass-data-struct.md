---
title: Estructura de CL_PASS_DATA
description: El C++ SDK de Build insights CL_PASS_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3df5b5bc1cddbadc4a4d432ae021dd8b338c532e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335259"
---
# <a name="cl_pass_data-structure"></a>Estructura de CL_PASS_DATA

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura `CL_PASS_DATA` describe un paso de compilación.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct CL_PASS_DATA_TAG
{
    int                         TranslationUnitPassCode;
    const wchar_t*              InputSourcePath;
    const wchar_t*              OutputObjectPath;

} CL_PASS_DATA;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `TranslationUnitPassCode` | Código que identifica el paso de compilación que se está ejecutando. Para obtener más información, vea [TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md). |
| `InputSourcePath` | El archivo de C++ código fuente C o en el que se está ejecutando este paso de compilación. |
| `OutputObjectPath` | El archivo objeto que genera el compilador. |

::: moniker-end
