---
title: Compilador advertencia (nivel 3) C4316 | Documentos de Microsoft
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
ms.openlocfilehash: 609f3bbe9f338c5d53491190512ce2b9c290cdb8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298387"
---
# <a name="compiler-warning-level-3-c4316"></a>Advertencia del compilador (nivel 3) C4316
Objeto que se asignan en el montón no puede estar alineado para este tipo.  
  
 Un objeto exceso alineado asignado mediante el uso de `operator new` posible que no tenga la alineación especificadas. Invalidar [new (operador)](../../c-runtime-library/operator-new-crt.md) y [operador delete](../../c-runtime-library/operator-delete-crt.md) para exceso alineado tipos para que usen las rutinas de asignación alineadas, por ejemplo, [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) y [_aligned_free](../../c-runtime-library/reference/aligned-free.md). El ejemplo siguiente genera C4316:  
  
```cpp  
// C4316.cpp  
// Test: cl /W3 /c C4316.cpp  
  
__declspec(align(32)) struct S {}; // C4324  
  
int main() {  
    new S; // C4316  
}  
```