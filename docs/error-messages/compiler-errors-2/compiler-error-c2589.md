---
title: Error del compilador C2589 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2589
dev_langs:
- C++
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c15589358979f554a9c17114f7d78b05dd83c472
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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