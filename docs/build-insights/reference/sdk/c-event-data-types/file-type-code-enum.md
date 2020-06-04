---
title: FILE_TYPE_CODE enum
description: El SDK de C++ Build Insights FILE_TYPE_CODE referencia de enumeración.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: dea603a072d7b2f472112a75b2e9ccded78399a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325562"
---
# <a name="file_type_code-enum"></a>FILE_TYPE_CODE enum

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `FILE_TYPE_CODE` enumeración describe el tipo de un archivo.

## <a name="members"></a>Miembros

| Nombre | Value | Descripción |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0 (0x00000000) | Un tipo de archivo que no aparece en esta enumeración. |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | Un archivo\*de objeto ( .obj). |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2 (0x00000002) | Un archivo\*ejecutable ( .exe) o DLL (\*.dll). |
| `FILE_TYPE_CODE_LIB` | 3 (0x00000003) | Un archivo de biblioteca estática (*.lib). |
| `FILE_TYPE_CODE_IMP_LIB` | 4 (0x00000004) | Una biblioteca de importación (*.lib) |
| `FILE_TYPE_CODE_EXP` | 5 (0x00000005) | Un archivo de exportación (*.exp). |

## <a name="remarks"></a>Observaciones

::: moniker-end
