---
title: Compilador advertencia (nivel 1) C4353 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4353
dev_langs:
- C++
helpviewer_keywords:
- C4353
ms.assetid: 6e79f186-ed82-4c95-9923-0ad5bb9c4db1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7b9974635fabc07f17b9e46b16d163c72b6d3ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278039"
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