---
title: "Error del compilador C2247 | Microsoft Docs"
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
  - "C2247"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2247"
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2247
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se puede tener acceso a 'identificador' porque 'clase' utiliza 'especificador' para heredar de 'clase'  
  
 `identifier` se hereda de una clase declarada con acceso privado o protegido.  
  
 El código siguiente genera el error C2247:  
  
```  
// C2247.cpp  
class A {  
public:  
   int i;  
};  
class B : private A {};    // B inherits a private A  
class C : public B {} c;   // so even though C's B is public  
int j = c.i;               // C2247, i not accessible  
```  
  
 Este error también se puede producir como resultado del trabajo de compatibilidad del compilador realizado para Visual Studio .NET 2003: control de acceso con miembros protegidos .  Sólo se puede tener acceso a un miembro protegido \(n\) mediante una función miembro de una clase \(B\) que hereda de la clase \(A\) de la que es \(n\) miembro.  
  
 Para que el código sea válido en las versiones Visual Studio .NET 2003 y Visual Studio .NET de Visual C\+\+, declare el miembro como friend del tipo.  También es posible utilizar la herencia pública.  
  
```  
// C2247b.cpp  
// compile with: /c  
// C2247 expected  
class A {  
public:  
   void f();  
   int n;  
};  
  
class B: protected A {  
   // Uncomment the following line to resolve.  
   // friend void A::f();  
};  
  
void A::f() {  
   B b;  
   b.n;  
}  
```  
  
 C2247 también se puede producir como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003. ahora no se puede tener acceso a las clases base.  Una clase \(A\) que es una clase base privada para un tipo \(B\) no debería ser accesible para un tipo \(C\) que utiliza B como clase base.  
  
 Para que el código sea válido en las versiones Visual Studio .NET 2003 y Visual Studio .NET de Visual C\+\+, utilice el operador de ámbito.  
  
```  
// C2247c.cpp  
// compile with: /c  
struct A {};  
  
struct B: private A {};  
  
struct C : B {  
   void f() {  
      A *p1 = (A*) this;   // C2247  
      // try the following line instead  
      // ::A *p2 = (::A*) this;  
   }  
};  
```