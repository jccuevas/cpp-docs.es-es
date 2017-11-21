---
title: "La resolución de nombres para los tipos dependientes | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3ca2c849c7ab825dfdfa609d680851de5432f012
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="name-resolution-for-dependent-types"></a>Resolución de nombres para los tipos dependientes
Use **typename** para los nombres completos en definiciones de plantilla para indicar al compilador que el nombre completo dado identifica un tipo. Para obtener más información, consulte [typename](../cpp/typename.md).  
  
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
  
```Output  
Name resolved by using typename keyword.  
```  
  
 Búsqueda de nombres para los nombres dependientes examina los nombres en el contexto de la definición de plantilla, en el ejemplo siguiente, este contexto encontraría `myFunction(char)`y el contexto de la creación de instancias de plantilla. En el ejemplo siguiente, se crea una instancia de la plantilla en main; por lo tanto, la `MyNamespace::myFunction` visible desde el punto de creación de instancias y se ha seleccionado como la mejor coincidencia. Si `MyNamespace::myFunction` cambiase de nombre, se llamaría a `myFunction(char)` en su lugar.  
  
 Todos los nombres se resuelven como si fueran nombres dependientes. Sin embargo, recomendamos utilizar nombres completos si hay alguna posibilidad de conflicto.  
  
```cpp  
// template_name_resolution2.cpp  
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
  
### <a name="output"></a>Salida  
  
```  
Int MyNamespace::myFunction  
```  
  
### <a name="template-disambiguation"></a>Desambiguación de plantilla  
 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] aplica las reglas del estándar C++98/03/11 para la desambiguación de la palabra clave “template”. En el ejemplo siguiente, Visual C++ 2010 aceptaría las líneas no conformes y las líneas que cumplen.  [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)]acepta sólo las líneas que cumplen.  
  
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
  
 Se requiere la conformidad con las reglas de desambiguación, porque, de forma predeterminada, C++ supone que `AY::Rebind` no es una plantilla, por lo que el compilador interpreta el siguiente “`<`” como "menos que". Debe saber que `Rebind` es una plantilla para que pueda analizar correctamente “`<`” como un corchete angular.  
  
## <a name="see-also"></a>Vea también  
 [Resolución de nombres](../cpp/templates-and-name-resolution.md)