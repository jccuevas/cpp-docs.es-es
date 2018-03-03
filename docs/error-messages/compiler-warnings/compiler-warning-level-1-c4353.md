---
title: Compilador advertencia (nivel 1) C4353 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4353
dev_langs:
- C++
helpviewer_keywords:
- C4353
ms.assetid: 6e79f186-ed82-4c95-9923-0ad5bb9c4db1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8dd3ec65dac6720509b9c918f272d2eb6ff2720c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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