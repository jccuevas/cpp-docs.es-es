---
title: Error del compilador C3736 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3736
dev_langs: C++
helpviewer_keywords: C3736
ms.assetid: 579b773c-41e7-40ea-8382-2e3ce2667f4c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0c2d7f548a1795221a72d0ac7be01e8ed87fa6ce
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3736"></a>Error del compilador C3736
'evento': debe ser un método o, en el caso de eventos administrados, opcionalmente un miembro de datos  
  
 Nativos y eventos COM deben ser métodos. Los eventos de .NET también pueden ser miembros de datos.  
  
 El ejemplo siguiente genera C3736:  
  
```  
// C3736.cpp  
struct A {  
   __event int e();  
};  
  
struct B {  
   int f;   // C3736  
   // The following line resolves the error.  
   // int f();  
   B(A* a) {  
      __hook(&A::e, a, &B::f);  
   }  
};  
  
int main() {  
}  
```