---
title: Advertencia de las herramientas del vinculador LNK4254
ms.date: 11/04/2016
f1_keywords:
- LNK4254
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
ms.openlocfilehash: 8431bd2d89fd5df5cf076ad006ab04006f552c4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988066"
---
# <a name="linker-tools-warning-lnk4254"></a>Advertencia de las herramientas del vinculador LNK4254

sección ' section1 ' (desplazamiento) combinada en ' section2 ' (desplazamiento) con atributos diferentes

El contenido de una sección se combinó en otro, pero los atributos de las dos secciones son diferentes. El programa puede producir resultados inesperados. Por ejemplo, los datos que deseaba leer solo pueden estar ahora en una sección grabable.

Para resolver LNK4254, modifique o quite la solicitud Merge.

Cuando el destino es máquinas x86 y Windows CE destinos (ARM, MIPS, SH4 y Thumb) con Visual C++,. La sección CRT es de solo lectura. Si el código depende del comportamiento anterior (. Las secciones de CRT son de lectura/escritura, por lo que podría ver un comportamiento inesperado.

Para obtener más información, vea

- [/MERGE (Combinar secciones)](../../build/reference/merge-combine-sections.md)

- [comment (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera LNK4254.

```cpp
// LNK4254.cpp
// compile with: /W1 /link /WX
// LNK4254 expected
#pragma comment(linker, "/merge:.data=.text")
int main() {}
```
