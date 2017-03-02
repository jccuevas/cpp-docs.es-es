---
title: Compilador advertencia (nivel 1) C4319 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4319
dev_langs:
- C++
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
caps.latest.revision: 7
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: ca89431bfa263967462325b9e2ad2354d59bc989
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4319"></a>Advertencia del compilador (nivel 1) C4319
'operator': extensión de cero de tipo 'type' a un tipo 'type' de mayor tamaño  
  
 Al resultado del operador ~ (complemento bit a bit) se le quita el signo y, a continuación, se completa con ceros cuando se convierte a un tipo mayor.  
  
 En el ejemplo siguiente, ~(a - 1) se evalúa como una expresión de tipo long sin signo de 32 bits y, a continuación, se convierte a 64 bits mediante extensión con ceros. Esto podría producir resultados de operación inesperados.  
  
```  
// C4319.cpp  
// compile with: cl /W4 C4319.cpp  
int main() {  
   unsigned long a = 0;  
   unsigned long long q = 42;  
   q = q & ~(a - 1);    // C4319 expected  
}  
```
