---
title: Compilador advertencia (nivel 3) C4316 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4316
dev_langs:
- C++
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 5647c3ca9dbbd854c83398820575137c4032d3c6
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-3-c4316"></a>Advertencia del compilador (nivel 3) C4316
No se puede alinear asignado en el montón de objeto para este tipo.  
  
 Un objeto alineado exceso asignado mediante `operator new` no tenga la alineación especificadas. Invalidar [operador new](../../c-runtime-library/operator-new-crt.md) y [operador delete](../../c-runtime-library/operator-delete-crt.md) de exceso alineado tipos para que usen las rutinas de asignación alineadas, por ejemplo, [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) y [_aligned_free](../../c-runtime-library/reference/aligned-free.md). El ejemplo siguiente genera C4316:  
  
```cpp  
// C4316.cpp  
// Test: cl /W3 /c C4316.cpp  
  
__declspec(align(32)) struct S {}; // C4324  
  
int main() {  
    new S; // C4316  
}  
```
