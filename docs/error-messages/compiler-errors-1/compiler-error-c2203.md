---
title: Error del compilador C2203 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2203
dev_langs:
- C++
helpviewer_keywords:
- C2203
ms.assetid: 5497df43-86f6-43d5-b6cb-723c4c589b10
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: ebb6260cbf41ffcd48ef60a1bd183e27db17e16a
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2203"></a>Error del compilador C2203
Eliminar operador no puede especificar límites de matriz  
  
 Con el **/Za** opción (ANSI), el `delete` operador puede eliminar una matriz completa pero no partes o miembros específicos de la matriz.  
  
 El ejemplo siguiente genera C2203:  
  
```  
// C2203.cpp  
// compile with: /Za  
int main() {  
   int *ar = new int[10];  
   delete [4] ar;   // C2203  
   // try the following line instead  
   // delete [] ar;  
}  
```
