---
title: "Resoluci&#243;n de nombres para los tipos dependientes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Resoluci&#243;n de nombres para los tipos dependientes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice **typename** para los nombres completos en definiciones de plantilla, para indicar al compilador que el nombre completo dado identifica un tipo.  Para obtener más información, vea [typename](../cpp/typename.md).  
  
```cpp  
// template_name_resolution1.cpp  
#include <stdio.h>  
template <class T> class X  
{  
public:  
   void f(typename T::myType* mt) {}  
};  
  
class Yarg  
{  
public:  
   struct myType { };  
};  
  
int main()  
{  
   X<Yarg> x;  
   x.f(new Yarg::myType());  
   printf("Name resolved by using typename keyword.");  
}  
```  
  
### Salida  
  
```  
Name resolved by using typename keyword.  
```  
  
 La búsqueda de nombre para los nombres dependientes examina los nombres en el contexto de la definición de la plantilla \(en el ejemplo siguiente, este contexto encontraría `myFunction(char)`\) y el contexto de la creación de instancias de la plantilla.  En el ejemplo siguiente, se crean instancias de la plantilla en main; por consiguiente, `MyNamespace::myFunction` es visible desde el punto de creación de las instancias, y se elige como la mejor coincidencia.  Si `MyNamespace::myFunction` cambiase de nombre, se llamaría a `myFunction(char)` en su lugar.  
  
 Todos los nombres se resuelven como si fueran nombres dependientes.  Sin embargo, recomendamos utilizar nombres completos si hay alguna posibilidad de conflicto.  
  
```cpp  
//template_name_resolution2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
void myFunction(char)  
{  
   cout << "Char myFunction" << endl;  
}  
  
template <class T> class Class1  
{  
public:  
   Class1(T i)  
   {  
      // If replaced with myFunction(1), myFunction(char)  
      // will be called  
      myFunction(i);  
}  
};  
  
namespace MyNamespace  
{  
   void myFunction(int)  
   {  
      cout << "Int MyNamespace::myFunction" << endl;  
   }  
};  
  
using namespace MyNamespace;  
  
int main()  
{  
   Class1<int>* c1 = new Class1<int>(100);  
}  
```  
  
### Salida  
  
```  
Int MyNamespace::myFunction  
```  
  
### Desambiguación de plantilla  
 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] aplica las reglas del estándar C\+\+98\/03\/11 para la desambiguación de la palabra clave “template”.  En el ejemplo siguiente, [!INCLUDE[cpp_dev10_long](../build/includes/cpp_dev10_long_md.md)] aceptaría las líneas no conformes y las líneas que cumplen. [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] solo acepta las líneas que cumplen.  
  
```cpp  
#include <iostream>  
#include <ostream>  
#include <typeinfo>  
using namespace std;  
  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    #if defined(NONCONFORMANT)  
        typedef typename AY::Rebind<X>::Other AX; // nonconformant  
    #elif defined(CONFORMANT)  
        typedef typename AY::template Rebind<X>::Other AX; // conformant  
    #else  
        #error Define NONCONFORMANT or CONFORMANT.  
    #endif  
};  
  
int main() {  
    cout << typeid(Container<int, Allocator<float>>::AX).name() << endl;  
}  
```  
  
 Se requiere la conformidad con las reglas de desambiguación, porque, de forma predeterminada, C\+\+ supone que `AY::Rebind` no es una plantilla, por lo que el compilador interpreta el siguiente “`<`” como "menos que".  Debe saber que `Rebind` es una plantilla para que pueda analizar correctamente “`<`” como un corchete angular.  
  
## Vea también  
 [Resolución de nombres](../cpp/templates-and-name-resolution.md)