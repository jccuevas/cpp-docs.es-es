---
title: -IMPORTS (DUMPBIN) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /imports
dev_langs:
- C++
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5b3b1e3a74fea278bc142d02f793308b6b0e054
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713575"
---
# <a name="imports-dumpbin"></a>/IMPORTS (DUMPBIN)

```
/IMPORTS[:file]
```

Esta opción muestra la lista de DLL (tanto los vinculados estáticamente y [cargado retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)) que se importan en un archivo ejecutable o DLL y todas las importaciones individuales de cada uno de estos archivos DLL.

El elemento opcional `file` especificación le permite especificar que se mostrará las importaciones para solo ese archivo DLL. Por ejemplo:

```
dumpbin /IMPORTS:msvcrt.dll
```

## <a name="remarks"></a>Comentarios

Los resultados mostrados por esta opción son similar a la [/EXPORTA](../../build/reference/dash-exports.md) salida.

Solo el [/HEADERS](../../build/reference/headers.md) está disponible para su uso en los archivos producidos con la opción de DUMPBIN el [/GL](../../build/reference/gl-whole-program-optimization.md) opción del compilador.

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)