---
title: Advertencia del compilador (nivel 3) C4316
ms.date: 11/04/2016
f1_keywords:
- C4316
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
ms.openlocfilehash: 5f895a231c8b32d76e4ccd3c15ffae5717d8017f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476068"
---
# <a name="compiler-warning-level-3-c4316"></a>Advertencia del compilador (nivel 3) C4316

No se puede alinear asignado en el montón de objeto para este tipo.

Un objeto demasiado alineado asignado mediante `operator new` no puede tener la alineación especificada. Invalidar [new (operador)](../../c-runtime-library/operator-new-crt.md) y [operador delete](../../c-runtime-library/operator-delete-crt.md) para los tipos demasiado alineados para que usen las rutinas de asignación alineadas, por ejemplo, [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) y [_aligned_free](../../c-runtime-library/reference/aligned-free.md). El ejemplo siguiente genera C4316:

```cpp
// C4316.cpp
// Test: cl /W3 /c C4316.cpp

__declspec(align(32)) struct S {}; // C4324

int main() {
    new S; // C4316
}
```