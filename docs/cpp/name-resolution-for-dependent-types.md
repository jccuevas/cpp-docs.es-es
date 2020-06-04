---
title: Resolución de nombres para los tipos dependientes
ms.date: 11/04/2016
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
ms.openlocfilehash: e9954eab2793f9adf0de75775563df0ae6f063f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161161"
---
# <a name="name-resolution-for-dependent-types"></a>Resolución de nombres para los tipos dependientes

Use **TypeName** para nombres completos en las definiciones de plantilla para indicar al compilador que el nombre completo especificado identifica un tipo. Para obtener más información, consulte [TypeName](../cpp/typename.md).

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

La búsqueda de nombre para los nombres dependientes examina los nombres desde el contexto de la definición de plantilla, en el ejemplo siguiente, este contexto encontraría `myFunction(char)`, y el contexto de la creación de instancias de la plantilla. En el ejemplo siguiente, se crea una instancia de la plantilla en Main; por lo tanto, el `MyNamespace::myFunction` es visible desde el punto de creación de instancias y se selecciona como la mejor coincidencia. Si `MyNamespace::myFunction` cambiase de nombre, se llamaría a `myFunction(char)` en su lugar.

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

### <a name="output"></a>Output

```Output
Int MyNamespace::myFunction
```

### <a name="template-disambiguation"></a>Desambiguación de plantilla

Visual Studio 2012 aplica las reglas estándar de C++ 98/03/11 para la anulación de ambigüedades con la palabra clave "template". En el ejemplo siguiente, Visual Studio 2010 aceptaría las líneas no compatibles y las líneas de ajuste.  Visual Studio 2012 solo acepta las líneas de ajuste.

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

## <a name="see-also"></a>Consulte también

[Resolución de nombres](../cpp/templates-and-name-resolution.md)
