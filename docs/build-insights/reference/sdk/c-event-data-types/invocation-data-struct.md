---
title: Estructura de INVOCATION_DATA
description: El C++ SDK de Build insights INVOCATION_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b2e8ddcf79201d8bcbbb8eb298b96b5c7680f90e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335145"
---
# <a name="invocation_data-structure"></a>Estructura de INVOCATION_DATA

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura `INVOCATION_DATA` describe una invocación del compilador o del enlazador.

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
| `MSVCToolCode` | Código que identifica el tipo de la invocación. Para obtener más información, vea [MSVC_TOOL_CODE](msvc-tool-code-enum.md). |
| `ToolVersion` | Objeto que almacena la versión de la herramienta invocada como un grupo de valores enteros. |
| `ToolVersionString` | Describe la versión de la herramienta invocada en forma de texto. |
| `WorkingDirectory` | Directorio desde el que se realizó la invocación. |
| `ToolPath` | La ruta de acceso absoluta de la herramienta invocada. |

::: moniker-end
