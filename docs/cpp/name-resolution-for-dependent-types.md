---
title: Resolución de nombres para los tipos dependientes
ms.date: 11/04/2016
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
ms.openlocfilehash: 04db4b0efc5e58dbd3de6fc9979c3a3cdd44d84e
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345936"
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

Búsqueda de nombres para los nombres dependientes examina los nombres en el contexto de la definición de plantilla, en el ejemplo siguiente, este contexto encontraría `myFunction(char)`y el contexto de la creación de instancias de plantilla. En el ejemplo siguiente, se crea una instancia de la plantilla en main; por lo tanto, el `MyNamespace::myFunction` es visible desde el punto de creación de instancias y se elige como la mejor coincidencia. Si `MyNamespace::myFunction` cambiase de nombre, se llamaría a `myFunction(char)` en su lugar.

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

```Output
Int MyNamespace::myFunction
```

### <a name="template-disambiguation"></a>Desambiguación de plantilla

Visual Studio 2012 exige la C ++ 98/03/11 reglas estándar para la Desambiguación de la palabra clave "template". En el ejemplo siguiente, Visual C++ 2010 aceptaría las líneas no conformes y las líneas que cumplen.  Visual Studio 2012 acepta solo las líneas que cumplen.

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