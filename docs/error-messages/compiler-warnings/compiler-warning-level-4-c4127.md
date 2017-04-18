---
title: Compilador advertencia (nivel 4) C4127 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4127
dev_langs:
- C++
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 3e9fb4ed25e51311ec4f6b1d71a249c21d466069
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-4-c4127"></a>Advertencia del compilador (nivel 4) C4127
la expresión condicional es constante  
  
 La expresión de control de una instrucción `if` o un bucle `while` se evalúa como una constante. Debido a su uso idiomática comunes, constantes triviales, como 1 o `true` desencadenar la advertencia, a menos que sean resultado de una operación en una expresión. Si la expresión de control de un `while` bucle es una constante porque se sale del bucle en el centro, considere la posibilidad de reemplazar el `while` en bucle con un `for` bucle. Se puede omitir la inicialización, la prueba de terminación y el incremento de un `for` bucle, lo cual hace que el bucle infinito, al igual que `while(1)`, y puede salir del bucle desde el cuerpo de la `for` instrucción.  
  
 El ejemplo siguiente muestra dos maneras C4127 se genera y muestra cómo utilizar un bucle for para evitar la advertencia:  
  
```  
// C4127.cpp  
// compile with: /W4  
#include <stdio.h>  
int main() {  
   if (1 == 1) {}   // C4127  
   while (42) { break; }   // C4127  
  
   // OK  
   for ( ; ; ) {  
      printf("test\n");  
      break;  
   }  
}  
```
