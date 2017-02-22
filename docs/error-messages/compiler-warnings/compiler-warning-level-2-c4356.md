---
title: "Advertencia del compilador (nivel 2) C4356 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4356"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4356"
ms.assetid: 3af3defe-de33-43b6-bd6c-2c2e09e34f3f
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Advertencia del compilador (nivel 2) C4356
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'miembro': no se puede inicializar el miembro de datos estático mediante una clase derivada  
  
 La inicialización de un miembro de datos estático estaba mal formada.  El compilador ha aceptado la inicialización.  
  
 Éste es un cambio importante en el compilador de Visual C\+\+ .NET 2003.  
  
 Para que el código funcione de igual forma en todas las versiones de Visual C\+\+, inicialice el miembro mediante la clase base.  
  
 Utilice el pragma [warning](../../preprocessor/warning.md) para deshabilitar esta advertencia.  
  
 El código siguiente genera el error C4356:  
  
```  
// C4356.cpp  
// compile with: /W2 /EHsc  
#include <iostream>  
  
template <class T>  
class C {  
   static int n;  
};  
  
class D : C<int> {};  
  
int D::n = 0; // C4356  
// try the following line instead  
// int C<int>::n = 0;  
  
class A {  
public:  
   static int n;  
};  
  
class B : public A {};  
  
int B::n = 10;   // C4356  
// try the following line instead  
// int A::n = 99;  
  
int main() {  
   using namespace std;  
   cout << B::n << endl;  
}  
```