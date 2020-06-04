---
title: Advertencia del compilador (nivel 3) C4316
ms.date: 11/04/2016
f1_keywords:
- C4316
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
ms.openlocfilehash: 0d920cb3dc967854d1a507d06ce31fde6a670434
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198853"
---
# <a name="compiler-warning-level-3-c4316"></a>Advertencia del compilador (nivel 3) C4316

Es posible que el objeto asignado en el montón no esté alineado para este tipo.

Un objeto sobrealineado asignado mediante `operator new` puede no tener la alineación especificada. Invalide los [operadores New](../../c-runtime-library/operator-new-crt.md) y [Delete](../../c-runtime-library/operator-delete-crt.md) para los tipos que se alinean en exceso para que usen las rutinas de asignación alineadas, por ejemplo, [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) y [_aligned_free](../../c-runtime-library/reference/aligned-free.md). En el ejemplo siguiente se genera C4316:

```cpp
// C4316.cpp
// Test: cl /W3 /c C4316.cpp

__declspec(align(32)) struct S {}; // C4324

int main() {
    new S; // C4316
}
```
