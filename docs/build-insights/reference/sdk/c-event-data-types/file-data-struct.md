---
title: estructura FILE_DATA
description: El SDK de C++ Build Insights FILE_DATA referencia de estructura.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6b7b0129c54fa4b1d5285bafb38761da45bab4e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325586"
---
# <a name="file_data-structure"></a>estructura FILE_DATA

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `FILE_DATA` estructura describe una entrada o salida de archivo.

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
| `Path` | Ruta absoluta del archivo |
| `TypeCode` | Código que describe el tipo del archivo. Para obtener más información, consulte [FILE_TYPE_CODE](file-type-code-enum.md). |

::: moniker-end
