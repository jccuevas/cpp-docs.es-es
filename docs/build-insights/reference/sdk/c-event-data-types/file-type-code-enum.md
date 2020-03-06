---
title: Enumeración FILE_TYPE_CODE
description: El C++ SDK de Build insights FILE_TYPE_CODE referencia de enumeración.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e64f9315c62ce40c436032d6c96fdfa725847a7f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335169"
---
# <a name="file_type_code-enum"></a>Enumeración FILE_TYPE_CODE

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La enumeración `FILE_TYPE_CODE` describe el tipo de un archivo.

## <a name="members"></a>Miembros

| Name | Valor | Descripción |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0 (0x00000000) | Un tipo de archivo no incluido en esta enumeración. |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | Un archivo de objeto (\*. obj). |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2 (0x00000002) | Archivo ejecutable (\*. exe) o DLL (\*. dll). |
| `FILE_TYPE_CODE_LIB` | 3 (0x00000003) | Un archivo de biblioteca estática (*. lib). |
| `FILE_TYPE_CODE_IMP_LIB` | 4 (0x00000004) | Una biblioteca de importación (*. lib) |
| `FILE_TYPE_CODE_EXP` | 5 (0x00000005) | Un archivo de exportación (*. exp). |

## <a name="remarks"></a>Comentarios

::: moniker-end
