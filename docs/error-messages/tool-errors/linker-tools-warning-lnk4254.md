---
title: Las herramientas del vinculador LNK4254 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4254
dev_langs:
- C++
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2ef421cbfa87ecab8a27dfa796eaa4eaacf7b70
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064654"
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