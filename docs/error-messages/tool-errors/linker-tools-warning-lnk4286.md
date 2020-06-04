---
title: Advertencia de las herramientas del vinculador LNK4286
ms.date: 04/15/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: d0205ba065f6e410383c38a0f1c2eaa0da55fe93
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173873"
---
# <a name="linker-tools-warning-lnk4286"></a>Advertencia de las herramientas del vinculador LNK4286

> '*filename_2. obj*' importa el símbolo '*Symbol*' definido en '*filename_1. obj*'

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) se especificó para *Symbol* , aunque el símbolo esté definido en el archivo objeto *filename_1. obj* en la misma imagen. Quite el modificador `__declspec(dllimport)` para resolver esta advertencia.

## <a name="remarks"></a>Observaciones

Warning LNK4286 es una versión más general de la [Advertencia de las herramientas del vinculador LNK4217](linker-tools-warning-lnk4217.md). El enlazador genera la advertencia LNK4286 cuando puede indicar qué archivo objeto hacía referencia al símbolo, pero no qué función.

Para resolver LNK4286, quite el modificador de la declaración `__declspec(dllimport)` de la declaración adelantada de *Symbol* a la que se hace referencia en *filename_2. obj*.

Aunque el código generado final se comporta correctamente, el código generado para llamar a una función importada es menos eficaz que llamar directamente a la función. Esta advertencia no aparece cuando se compila con la opción [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) .

Para obtener más información sobre las declaraciones de datos de importación y exportación, vea [dllexport, DllImport](../../cpp/dllexport-dllimport.md).

## <a name="see-also"></a>Consulte también

[Advertencia de las herramientas del vinculador LNK4049](linker-tools-warning-lnk4049.md) \
[Advertencia de las herramientas del vinculador LNK4217](linker-tools-warning-lnk4217.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
