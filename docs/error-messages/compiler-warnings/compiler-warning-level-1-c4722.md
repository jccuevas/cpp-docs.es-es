---
title: Compilador advertencia (nivel 1) C4722 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4722
dev_langs:
- C++
helpviewer_keywords:
- C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
caps.latest.revision: 6
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: a88d734f0f17437efe3b4a60a3439135b7feec4e
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4722"></a>Advertencia del compilador (nivel 1) C4722
'function': el destructor nunca devuelve un valor, posible pérdida de memoria  
  
 El flujo de control finaliza en un destructor. Se cerrará el subproceso o el programa completo y no se pueden liberar recursos asignados.  Además, si se llama un destructor para desenredar la pila durante el procesamiento de la excepción, el comportamiento del ejecutable es indefinido.  
  
 Para resolver el problema, quite la llamada de función que hace que el destructor no devuelva ningún valor.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4722:  
  
```  
// C4722.cpp  
// compile with: /O1 /W1 /c  
#include <stdlib.h>  
class C {  
public:  
   C();  
   ~C() { exit(1); };   // C4722  
};  
  
extern void func (C*);  
  
void Test(){  
   C x;  
   func(&x);  
   // control will not leave Test because destructor will exit  
}  
```
