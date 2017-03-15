---
title: "Advertencia del compilador (nivel 2) C4250 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4250"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4250"
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Advertencia del compilador (nivel 2) C4250
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase1' : hereda 'clase2::miembro' mediante dominación  
  
 Dos o más miembros tienen el mismo nombre.  El miembro de `class2` es heredado, porque es una clase base para las demás clases que contiene.  
  
 Para suprimir la advertencia C4250, utilice el pragma [warning](../../preprocessor/warning.md).  
  
 Dado que una clase base virtual se comparte entre varias clases derivadas, un nombre de una clase derivada domina un nombre de una clase base.  Por ejemplo, dada la siguiente jerarquía de clases, hay dos definiciones de funciones heredadas dentro del rombo: la instancia vbc::func\(\) mediante la clase débil, y la dominant::func\(\) mediante la clase dominante.  Una llamada incompleta de func\(\) a través de un objeto de clase de rombo siempre llama a la instancia dominate::func\(\).  Si la clase débil fuera a introducir una instancia de func\(\), ninguna definición dominaría y la llamada se marcaría como ambigua.  
  
```  
// C4250.cpp  
// compile with: /c /W2  
#include <stdio.h>  
struct vbc {  
   virtual void func() { printf("vbc::func\n"); }  
};  
  
struct weak : public virtual vbc {};  
  
struct dominant : public virtual vbc {  
   void func() { printf("dominant::func\n"); }  
};  
  
struct diamond : public weak, public dominant {};  
  
int main() {  
   diamond d;  
   d.func();   // C4250  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4250.  
  
```  
// C4250_b.cpp  
// compile with: /W2 /EHsc  
#include <iostream>  
using namespace std;  
class A {  
public:  
   virtual operator int () {  
      return 2;  
   }  
};  
  
class B : virtual public A {  
public:  
   virtual operator int () {  
      return 3;  
   }  
};  
  
class C : virtual public A {};  
  
class E : public B, public C {};   // C4250  
  
int main() {  
   E eObject;  
   cout << eObject.operator int() << endl;  
}  
```  
  
## Ejemplo  
 Este ejemplo muestra una situación más compleja.  El ejemplo siguiente genera el error C4250.  
  
```  
// C4250_c.cpp  
// compile with: /W2 /EHsc  
#include <iostream>  
using namespace std;  
  
class V {  
public:  
   virtual int f() {  
      return 1024;  
   }  
};  
  
class B : virtual public V {  
public:  
   int b() {  
      return f(); // B::b() calls V::f()  
   }  
};  
  
class M : virtual public V {  
public:  
   int f() {  
      return 7;  
   }  
};  
  
// because of dominance, f() is M::f() inside D,  
// changing the meaning of B::b's f() call inside a D  
class D : public B, public M {};   // C4250  
  
int main() {  
   D d;  
   cout << "value is: " << d.b();   // invokes M::f()  
}  
```