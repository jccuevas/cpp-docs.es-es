---
title: Advertencia de las herramientas del vinculador LNK4253
ms.date: 11/04/2016
f1_keywords:
- LNK4253
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
ms.openlocfilehash: c3f45880571e5c06f76d5f063ff993e2f6b2be9b
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988090"
---
# <a name="linker-tools-warning-lnk4253"></a>Advertencia de las herramientas del vinculador LNK4253

sección ' section1 ' no combinada en ' section2 '; ya se combinó en ' section3 '

El enlazador detectó varias solicitudes de combinación en conflicto. El enlazador omitirá una de las solicitudes.

Se encuentra una opción o directiva **/Merge** y la sección `from` ya se ha combinado en una sección diferente debido a una opción o directiva **/Merge** anterior (o debido a una combinación implícita del enlazador).

Para resolver LNK4253, quite una de las solicitudes Merge.

Cuando el destino es máquinas x86 y Windows CE destinos (ARM, MIPS, SH4 y Thumb) con Visual C++,. La sección CRT es ahora de solo lectura. Si el código depende del comportamiento anterior (. Las secciones de CRT son de lectura/escritura, por lo que podría ver un comportamiento inesperado.

Para obtener más información, vea

- [/MERGE (Combinar secciones)](../../build/reference/merge-combine-sections.md)

- [comment (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, se indica al enlazador que combine la `.rdata` sección dos veces, pero en secciones diferentes. En el ejemplo siguiente se genera LNK4253.

```cpp
// LNK4253.cpp
// compile with: /W1 /link /merge:.rdata=text2
// LNK4253 expected
#pragma comment(linker, "/merge:.rdata=.text")
int main() {}
```
