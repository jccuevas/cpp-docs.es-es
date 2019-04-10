---
title: Advertencia LNK4286 de las herramientas del vinculador
ms.date: 04/09/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: f4ab9104c68534eaf1278a6cacb91623c24a237b
ms.sourcegitcommit: 0ad3f4517e64900a2702dd3d366586f9e2bce2c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477642"
---
# <a name="linker-tools-warning-lnk4286"></a>Advertencia LNK4286 de las herramientas del vinculador

> símbolo '*símbolo*'definido en'*filename_1.obj*'se importa de forma'*filename_2.obj*'

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) se especificó para *símbolo* , aunque el símbolo está definido en el archivo objeto *filename_1.obj* en la misma imagen. Quitar el `__declspec(dllimport)` modificador para resolver esta advertencia.

## <a name="remarks"></a>Comentarios

Advertencia LNK4286 es una versión más general de [advertencia de las herramientas del vinculador LNK4217](linker-tools-warning-lnk4217.md). El vinculador genera la advertencia LNK4286 cuando puede indicar a qué archivo de objeto al que hace referencia el símbolo, pero no que la función.

Para resolver LNK4286, quite el `__declspec(dllimport)` modificador de la declaración de la declaración adelantada de *símbolo* que se hace referencia en *filename_2.obj*.

Aunque el código generado final se comporta correctamente, el código generado para llamar a una función importada es menos eficaz que llamar directamente a la función. Esta advertencia no aparece cuando se compila con la [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opción.

Para obtener más información en Importar y exportar las declaraciones de datos, vea [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="see-also"></a>Vea también

[Herramientas del vinculador LNK4049 de advertencia](linker-tools-warning-lnk4049.md) \
[Advertencia LNK4286 de las herramientas del vinculador](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)