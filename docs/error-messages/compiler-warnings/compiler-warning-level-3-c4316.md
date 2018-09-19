---
title: Compilador advertencia (nivel 3) C4316 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4316
dev_langs:
- C++
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4170481b95cca0d43aa03c776009a5030194a4c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032931"
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