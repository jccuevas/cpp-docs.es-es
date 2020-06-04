---
title: 'Cómo: Declarar controladores en tipos nativos'
ms.custom: get-started-article
ms.date: 11/04/2016
f1_keywords:
- gcroot
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
ms.openlocfilehash: 11dbc196a89a224afe02312fbe4dff99d8467f4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545040"
---
# <a name="how-to-declare-handles-in-native-types"></a>Cómo: Declarar controladores en tipos nativos

No se puede declarar un tipo de identificador en un tipo nativo. vcclr. h proporciona la plantilla de contenedor con seguridad de tipos `gcroot` para hacer referencia a un objeto C++ CLR del montón. Esta plantilla permite incrustar un identificador virtual en un tipo nativo y tratarlo como si fuera el tipo subyacente. En la mayoría de los casos, puede usar el objeto `gcroot` como el tipo incrustado sin ninguna conversión. Sin embargo, con [for each, en](../dotnet/for-each-in.md), tiene que usar `static_cast` para recuperar la referencia administrada subyacente.

La plantilla de `gcroot` se implementa mediante las funciones de la clase de valor System:: Runtime:: InteropServices:: GCHandle, que proporciona "handles" en el montón de recolección de elementos no utilizados. Tenga en cuenta que los propios controladores no se recolectan como elementos no utilizados y se liberan cuando ya no los usa el destructor en la clase `gcroot` (este destructor no se puede llamar manualmente). Si crea una instancia de un objeto `gcroot` en el montón nativo, debe llamar a delete en ese recurso.

El tiempo de ejecución mantendrá una asociación entre el identificador y el objeto CLR, al que hace referencia. Cuando el objeto CLR se mueve con el montón de recolección de elementos no utilizados, el identificador devolverá la nueva dirección del objeto. No es necesario anclar una variable antes de que se asigne a una `gcroot` plantilla.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo crear un objeto `gcroot` en la pila nativa.

```cpp
// mcpp_gcroot.cpp
// compile with: /clr
#include <vcclr.h>
using namespace System;

class CppClass {
public:
   gcroot<String^> str;   // can use str as if it were String^
   CppClass() {}
};

int main() {
   CppClass c;
   c.str = gcnew String("hello");
   Console::WriteLine( c.str );   // no cast required
}
```

```Output
hello
```

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo crear un objeto `gcroot` en el montón nativo.

```cpp
// mcpp_gcroot_2.cpp
// compile with: /clr
// compile with: /clr
#include <vcclr.h>
using namespace System;

struct CppClass {
   gcroot<String ^> * str;
   CppClass() : str(new gcroot<String ^>) {}

   ~CppClass() { delete str; }

};

int main() {
   CppClass c;
   *c.str = gcnew String("hello");
   Console::WriteLine( *c.str );
}
```

```Output
hello
```

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo usar `gcroot` para almacenar referencias a tipos de valor (no tipos de referencia) en un tipo nativo mediante `gcroot` en el tipo con conversión boxing.

```cpp
// mcpp_gcroot_3.cpp
// compile with: /clr
#include < vcclr.h >
using namespace System;

public value struct V {
   String^ str;
};

class Native {
public:
   gcroot< V^ > v_handle;
};

int main() {
   Native native;
   V v;
   native.v_handle = v;
   native.v_handle->str = "Hello";
   Console::WriteLine("String in V: {0}", native.v_handle->str);
}
```

```Output
String in V: Hello
```

## <a name="see-also"></a>Consulte también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
