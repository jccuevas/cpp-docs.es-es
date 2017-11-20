---
title: C2027 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2027
dev_langs: C++
helpviewer_keywords: C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2a2fec9194858127ca08ecc0a891a81a91de48fa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2027"></a>C2027 de Error del compilador
el uso de un tipo no definido 'type'  
  
 No se puede usar un tipo hasta que se define. Para resolver el error, asegúrese de que el tipo se define completamente antes de hacer referencia a él.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2027.  
  
```  
// C2027.cpp  
class C;  
class D {  
public:  
   void func() {  
   }  
};  
  
int main() {  
   C *pC;  
   pC->func();   // C2027  
  
   D *pD;  
   pD->func();  
}  
```  
  
## <a name="example"></a>Ejemplo  
 Es posible declarar un puntero a un tipo declarado pero indefinido.  Pero Visual C++ no permite una referencia a un tipo no definido.  
  
 El ejemplo siguiente genera C2027.  
  
```  
// C2027_b.cpp  
class A;  
A& CreateA();  
  
class B;  
B* CreateB();  
  
int main() {  
   CreateA();   // C2027  
   CreateB();   // OK  
}  
```