---
title: "Error del compilador C2249 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2249"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2249"
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C2249
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'miembro' : no existe ninguna ruta accesible a un miembro declarado en una 'clase' base virtual  
  
 El `member` se hereda de una estructura o una clase base `virtual` no pública.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2249.  
  
```  
// C2249.cpp  
class A {  
private:  
   void privFunc( void ) {};  
public:  
   void pubFunc( void ) {};  
};  
  
class B : virtual public A {} b;  
  
int main() {  
   b.privFunc();    // C2249, private member of A  
   b.pubFunc();    // OK  
}  
```  
  
## Ejemplo  
 El error C2249 también puede producirse si intenta asignar una secuencia de la Biblioteca estándar de C\+\+ a otra secuencia.  El ejemplo siguiente genera el error C2249.  
  
```  
// C2249_2.cpp  
#include <iostream>  
using namespace std;  
int main() {  
   cout = cerr;   // C2249  
   #define cout cerr;   // OK  
}  
```