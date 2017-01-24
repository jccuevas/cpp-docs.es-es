---
title: "Resoluci&#243;n de nombres declarados localmente | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 743b88f3-de11-48f4-ae83-931449ea3886
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Resoluci&#243;n de nombres declarados localmente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se puede hacer referencia al propio nombre de la pantalla con o sin argumentos de plantilla.  En el ámbito de una plantilla de clase, el nombre en sí hace referencia a la plantilla.  En el ámbito de una especialización de plantilla o especialización parcial, el nombre hace referencia a la especialización o especialización parcial.  También se puede hacer referencia a otras especializaciones o especializaciones parciales de la plantilla con los argumentos de plantilla adecuados.  
  
## Ejemplo  
 En el código siguiente se muestra que el nombre de una plantilla de clase A se interpreta de manera diferente en el ámbito de una especialización o especialización parcial.  
  
```  
// template_name_resolution3.cpp  
// compile with: /c  
template <class T> class A {  
   A* a1;   // A refers to A<T>  
   A<int>* a2;  // A<int> refers to a specialization of A.  
   A<T*>* a3;   // A<T*> refers to the partial specialization A<T*>.  
};  
  
template <class T> class A<T*> {  
   A* a4; // A refers to A<T*>.  
};  
  
template<> class A<int> {  
   A* a5; // A refers to A<int>.  
};  
```  
  
## Ejemplo  
 En el caso de un conflicto de nombres entre un parámetro de plantilla y otro objeto, el parámetro de plantilla se puede o no se puede ocultar.  Las reglas siguientes ayudarán a determinar la prioridad.  
  
 El parámetro de plantilla está dentro del ámbito desde el punto donde aparece por primera vez hasta el final de la plantilla de clase o función.  Si el nombre aparece de nuevo en la lista de argumentos de plantilla o en la lista de clases base, hace referencia al mismo tipo.  En C\+\+ estándar, no se puede declarar ningún otro nombre que sea idéntico al parámetro de plantilla en el mismo ámbito.  Una extensión de Microsoft permite que el parámetro de plantilla se vuelva a definir en el ámbito de la plantilla.  En el ejemplo siguiente se muestra cómo usar el parámetro de plantilla en la especificación base de una plantilla de clase.  
  
```  
// template_name_resolution4.cpp  
// compile with: /EHsc  
template <class T>  
class Base1 {};  
  
template <class T>  
class Derived1 : Base1<T> {};  
  
int main() {  
   // Derived1<int> d;  
}  
```  
  
## Ejemplo  
 Al definir las funciones miembro de una plantilla fuera de la plantilla de clase, se puede usar un nombre de parámetro de plantilla diferente.  Si la definición de la función miembro de la plantilla utiliza un nombre diferente para el parámetro de plantilla que la declaración, y el nombre utilizado en la definición está en conflicto con otro miembro de la declaración, el miembro de la declaración de plantilla tiene prioridad.  
  
```  
// template_name_resolution5.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class T> class C {  
public:  
   struct Z {  
      Z() { cout << "Z::Z()" << endl; }  
   };  
   void f();  
};  
  
template <class Z>  
void C<Z>::f() {  
   // Z refers to the struct Z, not to the template arg;  
   // Therefore, the constructor for struct Z will be called.  
   Z z;  
}  
  
int main() {  
   C<int> c;  
   c.f();  
}  
```  
  
  **Z::Z\(\)**   
## Ejemplo  
 Al definir una función de plantilla o una función miembro fuera del espacio de nombres en el que se declaró la plantilla, el argumento de plantilla tiene prioridad sobre los nombres de otros miembros del espacio de nombres.  
  
```  
// template_name_resolution6.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
namespace NS {  
   void g() { cout << "NS::g" << endl; }  
  
   template <class T> struct C {  
      void f();  
      void g() { cout << "C<T>::g" << endl; }  
   };  
};  
  
template <class T>  
void NS::C<T>::f() {  
   g(); // C<T>::g, not NS::g  
};  
  
int main() {  
   NS::C<int> c;  
   c.f();  
}  
```  
  
  **C\<T\>::g**   
## Ejemplo  
 En las definiciones que están fuera de la declaración de clase de plantilla, si una clase de plantilla tiene una clase base que no depende de un argumento de plantilla y si la clase base o uno de sus miembros tiene el mismo nombre que un argumento de plantilla, el nombre de la clase base o miembro oculta el argumento de plantilla.  
  
```  
// template_name_resolution7.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct B {  
   int i;  
   void print() { cout << "Base" << endl; }  
};  
  
template <class T, int i> struct C : public B {  
   void f();  
};  
  
template <class B, int i>  
void C<B, i>::f() {  
   B b;   // Base class b, not template argument.  
   b.print();  
   i = 1; // Set base class's i to 1.  
}  
  
int main() {  
   C<int, 1> c;  
   c.f();  
   cout << c.i << endl;  
}  
```  
  
  **Base**  
**1**   
## Vea también  
 [Resolución de nombres](../cpp/templates-and-name-resolution.md)