---
title: estructura CL_PASS_DATA
description: El SDK de C++ Build Insights CL_PASS_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b0a41e59068ade285f1ffa1a9ce13734ef5f1f32
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325709"
---
# <a name="cl_pass_data-structure"></a>estructura CL_PASS_DATA

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `CL_PASS_DATA` estructura describe un pase de compilación.

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
| `TranslationUnitPassCode` | Código que identifica el pase de compilación que se está ejecutando. Para obtener más información, consulte [TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md). |
| `InputSourcePath` | El archivo de origen C o C++ en el que se ejecuta este paso de compilación. |
| `OutputObjectPath` | El archivo de objeto generado por el compilador. |

::: moniker-end
