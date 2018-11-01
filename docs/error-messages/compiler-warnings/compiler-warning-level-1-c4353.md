---
title: Advertencia del compilador (nivel 1) C4353
ms.date: 11/04/2016
f1_keywords:
- C4353
helpviewer_keywords:
- C4353
ms.assetid: 6e79f186-ed82-4c95-9923-0ad5bb9c4db1
ms.openlocfilehash: 305c1156ae8dc664edba17287786db50bfabbd18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483712"
---
# <a name="compiler-warning-level-1-c4353"></a>Advertencia del compilador (nivel 1) C4353

ha utilizado una extensión no estándar: constante 0 como expresión de función. Utilice en su lugar '__noop' función intrínseca

No se puede usar la constante cero (0) como una expresión de función. Para obtener más información, consulte [__noop](../../intrinsics/noop.md).

El ejemplo siguiente genera C4353:

```
// C4353.cpp
// compile with: /W1
void MyPrintf(void){};
#define X 0
#if X
   #define DBPRINT MyPrint
#else
   #define DBPRINT 0   // C4353 expected
#endif
int main(){
DBPRINT();
}
```