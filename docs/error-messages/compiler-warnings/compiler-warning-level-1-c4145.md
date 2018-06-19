---
title: Compilador advertencia (nivel 1) C4145 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4145
dev_langs:
- C++
helpviewer_keywords:
- C4145
ms.assetid: 0440777a-cca2-4159-aff5-e67a254ad64a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5803c8fee49c294823da4ecdb2b04638b763c00
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277409"
---
# <a name="compiler-warning-level-1-c4145"></a>Advertencia del compilador (nivel 1) C4145
'expression1': expresión relacional como expresión switch; posible confusión con 'expression2'  
  
 Una instrucción `switch` utiliza una expresión relacional como su expresión de control, lo que resulta en un valor booleano para las instrucciones **case** . ¿Quiso decir *expression2*?  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4145:  
  
```  
// C4145.cpp  
// compile with: /W1  
int main() {  
   int i = 0;  
   switch(i == 1) {   // C4145, use i instead of i == 1 to resolve  
      case 1:  
         break;  
      default:  
         break;  
   }  
}  
```