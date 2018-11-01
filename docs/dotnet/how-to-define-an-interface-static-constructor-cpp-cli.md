---
title: 'Cómo: Definir un constructor estático de interfaz (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [C++]
- static constructors, interface
- interface static constructor
ms.assetid: 1f031cb2-e94f-43dc-819b-44cf2faaaa49
ms.openlocfilehash: 0617454e0957dccc7e28a5172a40273b5d93bede
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566392"
---
# <a name="how-to-define-an-interface-static-constructor-ccli"></a>Cómo: Definir un constructor estático de interfaz (C++/CLI)

Una interfaz puede tener un constructor estático, que se puede usar para inicializar a los miembros de datos estáticos.  Un constructor estático se llamará a lo sumo una vez y se llamará antes de la primera vez que se tiene acceso a un miembro estático de interfaz.

## <a name="example"></a>Ejemplo

```
// mcppv2_interface_class2.cpp
// compile with: /clr
using namespace System;

interface struct MyInterface {
   static int i;
   static void Test() {
      Console::WriteLine(i);
   }

   static MyInterface() {
      Console::WriteLine("in MyInterface static constructor");
      i = 99;
   }
};

ref class MyClass : public MyInterface {};

int main() {
   MyInterface::Test();
   MyClass::MyInterface::Test();

   MyInterface ^ mi = gcnew MyClass;
   mi->Test();
}
```

```Output
in MyInterface static constructor
99
99
99
```

## <a name="see-also"></a>Vea también

[clase de interfaz](../windows/interface-class-cpp-component-extensions.md)