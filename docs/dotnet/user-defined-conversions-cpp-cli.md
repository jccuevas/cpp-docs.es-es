---
title: Conversiones definidas por el usuario (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined conversions [C++]
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
ms.openlocfilehash: bb7a30382bc586f4d324d47ef6e6757fac83f5ae
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545136"
---
# <a name="user-defined-conversions-ccli"></a>Conversiones definidas por el usuario (C++/CLI)

En esta sección se describen las conversiones definidas por el usuario (UDC) cuando uno de los tipos de la conversión es una referencia o una instancia de un tipo de valor o un tipo de referencia.

## <a name="implicit-and-explicit-conversions"></a>Conversiones implícitas y explícitas

Una conversión definida por el usuario puede ser implícita o explícita.  Una UDC debe ser implícita si la conversión no produce una pérdida de información. De lo contrario, se debe definir una UDC explícita.

El constructor de una clase nativa se puede usar para convertir una referencia o un tipo de valor en una clase nativa.

Para obtener más información sobre las conversiones, vea [conversión boxing](../extensions/boxing-cpp-component-extensions.md) y [conversiones estándar](../cpp/standard-conversions.md).

```cpp
// mcpp_User_Defined_Conversions.cpp
// compile with: /clr
#include "stdio.h"
ref class R;
class N;

value class V {
   static operator V(R^) {
      return V();
   }
};

ref class R {
public:
   static operator N(R^);
   static operator V(R^) {
      System::Console::WriteLine("in R::operator N");
      return V();
   }
};

class N {
public:
   N(R^) {
      printf("in N::N\n");
   }
};

R::operator N(R^) {
   System::Console::WriteLine("in R::operator N");
   return N(nullptr);
}

int main() {
   // Direct initialization:
   R ^r2;
   N n2(r2);   // direct initialization, calls constructor
   static_cast<N>(r2);   // also direct initialization

   R ^r3;
   // ambiguous V::operator V(R^) and R::operator V(R^)
   // static_cast<V>(r3);
}
```

**Salida**

```Output
in N::N
in N::N
```

## <a name="convert-from-operators"></a>Operadores de Convertir desde

Los operadores Convert-from crean un objeto de la clase en la que se define el operador a partir de un objeto de alguna otra clase.

Standard C++ no admite operadores Convert-from; Standard C++ usa constructores para este propósito. Sin embargo, al usar tipos CLR, C++ visual proporciona compatibilidad sintáctica para llamar a los operadores Convert-from.

Para interoperar bien con otros lenguajes conformes a CLS, es posible que desee ajustar cada constructor unario definido por el usuario para una clase determinada con un operador Convert-from correspondiente.

Operadores Convert-from:

- Se definirán como funciones estáticas.

- Puede ser implícito (para las conversiones que no pierden precisión, como Short-to-int) o Explicit, cuando puede haber una pérdida de precisión.

- Devolverá un objeto de la clase contenedora.

- Debe tener el tipo "de" como tipo de parámetro único.

En el ejemplo siguiente se muestra un operador de conversión definido por el usuario (UDC) implícito y explícito.

```cpp
// clr_udc_convert_from.cpp
// compile with: /clr
value struct MyDouble {
   double d;

   MyDouble(int i) {
      d = static_cast<double>(i);
      System::Console::WriteLine("in constructor");
   }

   // Wrap the constructor with a convert-from operator.
   // implicit UDC because conversion cannot lose precision
   static operator MyDouble (int i) {
      System::Console::WriteLine("in operator");
      // call the constructor
      MyDouble d(i);
      return d;
   }

   // an explicit user-defined conversion operator
   static explicit operator signed short int (MyDouble) {
      return 1;
   }
};

int main() {
   int i = 10;
   MyDouble md = i;
   System::Console::WriteLine(md.d);

   // using explicit user-defined conversion operator requires a cast
   unsigned short int j = static_cast<unsigned short int>(md);
   System::Console::WriteLine(j);
}
```

**Salida**

```Output
in operator
in constructor
10
1
```

## <a name="convert-to-operators"></a>Operadores Convert-to

Los operadores Convert-to convierten un objeto de la clase en la que se define el operador a algún otro objeto. En el ejemplo siguiente se muestra un operador de conversión implícito, convertido a definido por el usuario:

```cpp
// clr_udc_convert_to.cpp
// compile with: /clr
using namespace System;
value struct MyInt {
   Int32 i;

   // convert MyInt to String^
   static operator String^ ( MyInt val ) {
      return val.i.ToString();
   }

   MyInt(int _i) : i(_i) {}
};

int main() {
   MyInt mi(10);
   String ^s = mi;
   Console::WriteLine(s);
}
```

**Salida**

```Output
10
```

Un operador de conversión para convertir en definido por el usuario explícito es adecuado para las conversiones que pueden perder datos de alguna manera. Para invocar un operador Convert-to explícito, se debe usar una conversión.

```cpp
// clr_udc_convert_to_2.cpp
// compile with: /clr
value struct MyDouble {
   double d;
   // convert MyDouble to Int32
   static explicit operator System::Int32 ( MyDouble val ) {
      return (int)val.d;
   }
};

int main() {
   MyDouble d;
   d.d = 10.3;
   System::Console::WriteLine(d.d);
   int i = 0;
   i = static_cast<int>(d);
   System::Console::WriteLine(i);
}
```

**Salida**

```Output
10.3
10
```

## <a name="to-convert-generic-classes"></a>Para convertir clases genéricas

Puede convertir una clase genérica en T.

```cpp
// clr_udc_generics.cpp
// compile with: /clr
generic<class T>
public value struct V {
   T mem;
   static operator T(V v) {
      return v.mem;
   }

   void f(T t) {
      mem = t;
   }
};

int main() {
   V<int> v;
   v.f(42);
   int i = v;
   i += v;
   System::Console::WriteLine(i == (42 * 2) );
}
```

**Salida**

```Output
True
```

Un constructor de conversión toma un tipo y lo usa para crear un objeto.  Solo se llama a un constructor de conversión con inicialización directa; las conversiones no invocarán constructores de conversión. De forma predeterminada, los constructores de conversión son explícitos para los tipos CLR.

```cpp
// clr_udc_converting_constructors.cpp
// compile with: /clr
public ref struct R {
   int m;
   char c;

   R(int i) : m(i) { }
   R(char j) : c(j) { }
};

public value struct V {
   R^ ptr;
   int m;

   V(R^ r) : ptr(r) { }
   V(int i) : m(i) { }
};

int main() {
   R^ r = gcnew R(5);

   System::Console::WriteLine( V(5).m);
   System::Console::WriteLine( V(r).ptr);
}
```

**Salida**

```Output
5
R
```

En este ejemplo de código, una función de conversión estática implícita hace lo mismo que un constructor de conversión explícito.

```
public value struct V {
   int m;
   V(int i) : m(i) {}
   static operator V(int i) {
      V v(i*100);
      return v;
   }
};

public ref struct R {
   int m;
   R(int i) : m(i) {}
   static operator R^(int i) {
      return gcnew R(i*100);
   }
};

int main() {
   V v(13);   // explicit
   R^ r = gcnew R(12);   // explicit

   System::Console::WriteLine(v.m);
   System::Console::WriteLine(r->m);

   // explicit ctor can't be called here: not ambiguous
   v = 5;
   r = 20;

   System::Console::WriteLine(v.m);
   System::Console::WriteLine(r->m);
}
```

**Salida**

```Output
13
12
500
2000
```

## <a name="see-also"></a>Consulte también

[Clases y structs](../extensions/classes-and-structs-cpp-component-extensions.md)
