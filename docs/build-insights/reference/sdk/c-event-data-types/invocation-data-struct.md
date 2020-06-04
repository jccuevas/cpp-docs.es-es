---
title: estructura INVOCATION_DATA
description: El SDK de C++ Build Insights INVOCATION_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4e1f428facac413d7a4a5c059452dd8cdb07be4c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325484"
---
# <a name="invocation_data-structure"></a>estructura INVOCATION_DATA

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `INVOCATION_DATA` estructura describe una invocación del compilador o del vinculador.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct INVOCATION_DATA_TAG
{
    int                         MSVCToolCode;

    INVOCATION_VERSION_DATA     ToolVersion;

    const char*                 ToolVersionString;
    const wchar_t*              WorkingDirectory;
    const wchar_t*              ToolPath;

} INVOCATION_DATA;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `MSVCToolCode` | Código que identifica el tipo de la invocación. Para obtener más información, consulte [MSVC_TOOL_CODE](msvc-tool-code-enum.md). |
| `ToolVersion` | Objeto que almacena la versión de la herramienta invocada como un grupo de valores enteros. |
| `ToolVersionString` | Describe la versión de la herramienta invocada en forma de texto. |
| `WorkingDirectory` | El directorio desde el que se realizó la invocación. |
| `ToolPath` | Ruta absoluta de la herramienta invocada. |

::: moniker-end
