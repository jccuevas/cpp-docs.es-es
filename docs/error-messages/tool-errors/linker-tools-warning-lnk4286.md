---
title: Advertencia de las herramientas del vinculador LNK4286
ms.date: 04/15/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: 43ed18808ba5ce632dd7dc7095f7bc30e4497ec9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352442"
---
# <a name="linker-tools-warning-lnk4286"></a>Advertencia de las herramientas del vinculador LNK4286

> símbolo '*símbolo*'definido en'*filename_1.obj*'se importa de forma'*filename_2.obj*'

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) se especificó para *símbolo* , aunque el símbolo está definido en el archivo objeto *filename_1.obj* en la misma imagen. Quitar el `__declspec(dllimport)` modificador para resolver esta advertencia.

## <a name="remarks"></a>Comentarios

Advertencia LNK4286 es una versión más general de [advertencia de las herramientas del vinculador LNK4217](linker-tools-warning-lnk4217.md). El vinculador genera la advertencia LNK4286 cuando puede indicar a qué archivo de objeto al que hace referencia el símbolo, pero no que la función.

Para resolver LNK4286, quite el `__declspec(dllimport)` modificador de la declaración de la declaración adelantada de *símbolo* que se hace referencia en *filename_2.obj*.

Aunque el código generado final se comporta correctamente, el código generado para llamar a una función importada es menos eficaz que llamar directamente a la función. Esta advertencia no aparece cuando se compila con la [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opción.

Para obtener más información en Importar y exportar las declaraciones de datos, vea [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="see-also"></a>Vea también

[Herramientas del vinculador LNK4049 de advertencia](linker-tools-warning-lnk4049.md) \
[Herramientas del vinculador LNK4217 de advertencia](linker-tools-warning-lnk4217.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)