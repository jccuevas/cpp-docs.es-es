---
title: Advertencia de las herramientas del vinculador LNK4254
ms.date: 11/04/2016
f1_keywords:
- LNK4254
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
ms.openlocfilehash: 2c68e49d58b0fd6b28607eb0ba78c092441f6f4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467020"
---
# <a name="linker-tools-warning-lnk4254"></a>Advertencia de las herramientas del vinculador LNK4254

sección 'sección1' (desplazamiento) combinada en 'section2' (desplazamiento) con atributos diferentes

El contenido de una sección que se combina con otra, pero los atributos de las dos secciones son diferentes. El programa puede provocar resultados inesperados. Por ejemplo, los datos que desea leer sólo ya se puede en una sección de escritura.

Para resolver LNK4254, modifique o quite la solicitud de combinación.

Cuando el destino es x86 máquinas y los destinos de Windows CE (ARM, MIPS, SH4 y control de posición) con Visual C++, el. Sección de CRT es de solo lectura. Si el código depende del comportamiento anterior (. Las secciones de CRT son de sólo lectura), podría obtener comportamientos inesperados.

Para obtener más información, vea

- [/MERGE (Combinar secciones)](../../build/reference/merge-combine-sections.md)

- [comment (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia LNK4254.

```
// LNK4254.cpp
// compile with: /W1 /link /WX
// LNK4254 expected
#pragma comment(linker, "/merge:.data=.text")
int main() {}
```