---
title: Error del compilador C2589 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2589
dev_langs:
- C++
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 5301caf0b52e61000a804e1d73b76343a8b7b2eb
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2589"></a>Error del compilador C2589
'identificador': símbolo no válido en el lado derecho de '::'  
  
 Si una clase, estructura o unión nombre aparece a la izquierda del operador de resolución de ámbito (dos puntos dobles), el símbolo (token) de la derecha debe ser una clase, estructura o miembro de unión. De lo contrario, cualquier identificador global puede aparecer a la derecha.  
  
 No se pueden sobrecargar el operador de resolución de ámbito.  
  
 El ejemplo siguiente genera C2589:  
  
```  
// C2589.cpp  
void Test(){}  
class A {};  
void operator :: ();   // C2589  
  
int main() {  
   ::Test();  
}  
```
