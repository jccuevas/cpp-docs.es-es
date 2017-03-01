---
title: Compilador advertencia (nivel 1) C4552 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4552
dev_langs:
- C++
helpviewer_keywords:
- C4552
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
caps.latest.revision: 6
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
ms.openlocfilehash: fc791c0576f8961f0de72a2677b1b48d8d86afdd
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4552"></a>Advertencia del compilador (nivel 1) C4552
'operador': operador no tiene ningún efecto; se esperaba un operador con efectos secundarios  
  
 Si una instrucción de expresión tiene un operador sin efecto como la parte superior de la expresión, probablemente es un error.  
  
 Para evitar esta advertencia, coloque la expresión entre paréntesis.  
  
 El ejemplo siguiente genera C4552:  
  
```  
// C4552.cpp  
// compile with: /W1  
int main() {  
   int i, j;  
   i + j;   // C4552  
   // try the following line instead  
   // (i + j);  
}  
```
