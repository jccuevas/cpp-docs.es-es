---
title: Estructura de FILE_DATA
description: El C++ SDK de Build insights FILE_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 72cae8c8eb81bdb8d94897c46c5af90c89e92ab4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335199"
---
# <a name="file_data-structure"></a>Estructura de FILE_DATA

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La estructura `FILE_DATA` describe un archivo de entrada o salida.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct FILE_DATA_TAG
{
    const wchar_t*      Path;
    int                 TypeCode;

} FILE_DATA;
```

## <a name="members"></a>Miembros

|  |  |
|--|--|
| `Path` | La ruta de acceso absoluta del archivo |
| `TypeCode` | Código que describe el tipo del archivo. Para obtener más información, vea [FILE_TYPE_CODE](file-type-code-enum.md). |

::: moniker-end
