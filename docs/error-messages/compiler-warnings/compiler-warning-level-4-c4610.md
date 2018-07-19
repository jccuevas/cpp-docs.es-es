---
title: Compilador advertencia (nivel 4) C4610 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4610
dev_langs:
- C++
helpviewer_keywords:
- C4610
ms.assetid: 23c1a16c-9ca9-4bf6-9911-a72b785560c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0a329ae6e58043f3a615a46ef5bb4bfe4f15a2e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294923"
---
# <a name="compiler-warning-level-4-c4610"></a>Advertencia del compilador (nivel 4) C4610
objeto 'clase' nunca se puede crear instancias - necesario constructor definido por el usuario  
  
 La clase no tiene ningún definido por el usuario o constructores predeterminados. No se realiza ninguna creación de instancias. El ejemplo siguiente genera C4610:  
  
```  
// C4610.cpp  
// compile with: /W4  
struct A {  
   int &j;  
  
   A& A::operator=( const A& );  
};   // C4610  
  
/* use this structure definition to resolve the warning  
struct B {  
   int &k;  
  
   B(int i = 0) : k(i) {  
   }  
  
   B& B::operator=( const B& );  
} b;  
*/  
  
int main() {  
}  
```