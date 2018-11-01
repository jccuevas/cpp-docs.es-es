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
ms.openlocfilehash: 4b5cd212589be04f5f9f3a5dd6d4496a8f5add2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464933"
---
# <a name="how-to-declare-handles-in-native-types"></a>Cómo: Declarar controladores en tipos nativos

No se puede declarar un tipo de identificador en un tipo nativo. vcclr.h proporciona la plantilla de contenedor seguro para el tipo `gcroot` para hacer referencia a un objeto CLR del montón de C++. Esta plantilla le permite incrustar un identificador virtual en un tipo nativo y tratarlo como si fuera el tipo subyacente. En la mayoría de los casos, puede usar el `gcroot` object como tipo incrustado sin realizar ninguna conversión. Sin embargo, con [para cada uno, en](../dotnet/for-each-in.md), tiene que usar `static_cast` para recuperar la referencia administrada subyacente.

El `gcroot` plantilla se implementa mediante las funciones de la clase de valor System::Runtime::InteropServices::GCHandle, que proporciona "handles" en el montón de recolección. Tenga en cuenta que los propios controladores no se recopila y se liberan cuando ya no esté en uso el destructor en el `gcroot` clase (este destructor no se puede llamar manualmente). Si crea instancias de un `gcroot` de objeto en el montón nativo, debe llamar a delete en ese recurso.

El tiempo de ejecución mantendrá una asociación entre el identificador y el objeto CLR, que hace referencia. Cuando se mueve el objeto CLR con el montón de recolección, el controlador devolverá la nueva dirección del objeto. Una variable no tiene que fijarse antes de asignarlo a un `gcroot` plantilla.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo crear un `gcroot` objeto en la pila nativa.

```
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

En este ejemplo se muestra cómo crear un `gcroot` objeto en el montón nativo.

```
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

En este ejemplo se muestra cómo usar `gcroot` incluir referencias a tipos de valor (no tipos de referencia) en un tipo nativo mediante el uso de `gcroot` en el tipo de conversión boxing.

```
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

## <a name="see-also"></a>Vea también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)