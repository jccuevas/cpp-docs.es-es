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
ms.openlocfilehash: c8b0f88b38eb657fe4d3916ef0df13972e985cbe
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810346"
---
# <a name="imports-dumpbin"></a>/IMPORTS (DUMPBIN)

```
/IMPORTS[:file]
```

Esta opción muestra la lista de DLL (tanto los vinculados estáticamente y [cargado retrasada](linker-support-for-delay-loaded-dlls.md)) que se importan en un archivo ejecutable o DLL y todas las importaciones individuales de cada uno de estos archivos DLL.

El elemento opcional `file` especificación le permite especificar que se mostrará las importaciones para solo ese archivo DLL. Por ejemplo:

```
dumpbin /IMPORTS:msvcrt.dll
```

## <a name="remarks"></a>Comentarios

Los resultados mostrados por esta opción son similar a la [/EXPORTA](dash-exports.md) salida.

Solo el [/HEADERS](headers.md) está disponible para su uso en los archivos producidos con la opción de DUMPBIN el [/GL](gl-whole-program-optimization.md) opción del compilador.

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](dumpbin-options.md)
