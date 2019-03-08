---
title: /IMPORTS (DUMPBIN)
ms.date: 11/04/2016
f1_keywords:
- /imports
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
ms.openlocfilehash: 94009670329887a0b8a35e7b8b36996a84c7faa6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417507"
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
