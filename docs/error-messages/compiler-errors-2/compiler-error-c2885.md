---
title: "Error del compilador C2885 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2885"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2885"
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2885
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase::identificador' : no es una declaración using válida en un ámbito de no clase  
  
 Se ha utilizado una declaración [using](../../cpp/using-declaration.md) incorrectamente.  
  
## Ejemplo  
 Este error se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual C\+\+ 2005: ya no es válido tener una declaración `using` de un tipo anidado; debe calificar explícitamente cada referencia realizada al tipo anidado, incluir el tipo en un espacio de nombres o crear una definición de tipos \(typedef\).  
  
 El ejemplo siguiente genera el error C2885.  
  
```  
// C2885.cpp  
namespace MyNamespace {  
   class X1 {};  
}  
  
struct MyStruct {  
   struct X1 {  
      int i;  
   };  
};  
  
int main () {  
   using MyStruct::X1;   // C2885  
  
   // OK  
   using MyNamespace::X1;  
   X1 myX1;  
  
   MyStruct::X1 X12;  
  
   typedef MyStruct::X1 abc;  
   abc X13;  
   X13.i = 9;  
}  
```  
  
## Ejemplo  
 Si utiliza la palabra clave `using` con un miembro de clase, C\+\+ necesita que defina el miembro dentro de otra clase \(una clase derivada\).  
  
 El ejemplo siguiente genera el error C2885.  
  
```  
// C2885_b.cpp  
// compile with: /c  
class A {  
public:  
   int i;  
};  
  
void z() {  
   using A::i;   // C2885 not in a class  
}  
  
class B : public A {  
public:  
   using A::i;  
};  
```