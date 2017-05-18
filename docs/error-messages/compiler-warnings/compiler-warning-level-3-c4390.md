---
title: Compilador C4390 de advertencia (nivel 3) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4390
dev_langs:
- C++
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
caps.latest.revision: 9
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
ms.openlocfilehash: dd04b9faa2ed1376b821dedb6270950e1b035df5
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-3-c4390"></a>Advertencia del compilador (nivel 3) C4390
';' : se encontró una instrucción controlada vacía; ¿es esa la intención?  
  
 Se encontró un punto y coma después de una instrucción de control que no contiene instrucciones.  
  
 Si se obtiene C4390 a causa de una macro, debe utilizar el [advertencia](../../preprocessor/warning.md) pragma para deshabilitar C4390 en el módulo que contiene la macro.  
  
 El ejemplo siguiente genera C4390:  
  
```  
// C4390.cpp  
// compile with: /W3  
int main() {  
   int i = 0;  
   if (i);   // C4390  
      i++;  
}  
```
