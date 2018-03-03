---
title: Compilador advertencia (nivel 1) C4822 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4822
dev_langs:
- C++
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 89ed0dc851726b7b543ed2b8e1a319cc2ac6756e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4822"></a>Advertencia del compilador (nivel 1) C4822
'member': la función miembro de clase local no tiene cuerpo  
  
 Una función de miembro de clase local se ha declarado, pero no se ha definido en la clase. Para usar una función de miembro de clase local, debe definirla en la clase. No se puede declarar en la clase y definirla fuera de ella.  
  
 Cualquier definición de la clase de una función miembro de clase local será un error.  
  
 El ejemplo siguiente genera la advertencia C4822:  
  
```  
// C4822.cpp  
// compile with: /W1  
int main() {  
   struct C {  
      void func1(int);   // C4822  
      // try the following line instead  
      // void func1(int){}  
  };  
}  
```