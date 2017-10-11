---
title: Error del compilador C3531 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3531
dev_langs:
- C++
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 7753e30e305b7b36adc3b4d2b535f755fa455bdd
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3531"></a>Error del compilador C3531
'símbolo': un símbolo cuyo tipo contiene 'auto' debe tener un inicializador  
  
 La variable especificada no tiene una expresión de inicializador.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Especifique una expresión de inicializador, como una asignación simple que usa la sintaxis de signo igual, al declarar la variable.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera el error C3531 porque las variables `x1`, `y1, y2, y3`, y `z2` no están inicializados.  
  
```  
// C3531.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto x1;                  // C3531  
   auto y1, y2, y3;          // C3531  
   auto z1 = 1, z2, z3 = -1; // C3531  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Auto (palabra clave)](../../cpp/auto-keyword.md)
