---
title: Compilador advertencia (nivel 1) C4441 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4441
dev_langs: C++
helpviewer_keywords: C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fc83284e7de2c381413dd48f60a82dd68942568f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4441"></a>Advertencia del compilador (nivel 1) C4441
convención de llamada de 'cc1' omitida; en su lugar, usó 'cc2'  
  
 Las funciones miembro de tipos administrados definidos por el usuario y tipos genéricos de la función global deben utilizar el [__clrcall](../../cpp/clrcall.md) convención de llamada.  El compilador utiliza `__clrcall`.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4441.  
  
```  
// C4441.cpp  
// compile with: /clr /W1 /c  
generic <class ItemType>  
void __cdecl Test(ItemType item) {}   // C4441  
// try the following line instead  
// void Test(ItemType item) {}  
  
ref struct MyStruct {  
   void __cdecl Test(){}   // C4441  
   void Test2(){}   // OK  
};  
```