---
title: "Advertencia del compilador (nivel 1) C4441 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4441"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4441"
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Advertencia del compilador (nivel 1) C4441
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

convención de llamada de 'cc1' omitida; se usó 'cc2' en su lugar  
  
 Las funciones miembro de los tipos administrados definidos por el usuario y los genéricos de funciones globales deben utilizar la convención de llamada [\_\_clrcall](../../cpp/clrcall.md).  El compilador utilizó `__clrcall`.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4441.  
  
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