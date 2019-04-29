---
title: /LINENUMBERS
ms.date: 11/04/2016
f1_keywords:
- /linenumbers
helpviewer_keywords:
- LINENUMBERS dumpbin option
- line numbers
- -LINENUMBERS dumpbin option
- /LINENUMBERS dumpbin option
ms.assetid: 1681d582-2c2f-484e-9920-109959549055
ms.openlocfilehash: ea4c3ac2ad582e0fe364f2da26511a66e9dc376c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269246"
---
# <a name="linenumbers"></a>/LINENUMBERS

```
/LINENUMBERS
```

## <a name="remarks"></a>Comentarios

Esta opción muestra los números de línea COFF. Existen números de línea en un archivo objeto si se compiló con la base de datos programa (/Zi), compatible con C7 (/ Z7), o sólo números de línea (/ Zd). Un archivo ejecutable o DLL contiene números de línea COFF si se ha vinculado con generar información de depuración (/Debug).

Solo el [/HEADERS](headers.md) está disponible para su uso en los archivos producidos con la opción de DUMPBIN el [/GL](gl-whole-program-optimization.md) opción del compilador.

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](dumpbin-options.md)
