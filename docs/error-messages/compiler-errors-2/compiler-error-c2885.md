---
title: Error del compilador C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: ff5e770052301e95f694d3712f95b82732c2faba
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447701"
---
# <a name="compiler-error-c2885"></a>Error del compilador C2885

'Class:: identifier': no es una declaración using válida en el ámbito de no clase

Ha utilizado un [mediante](../../cpp/using-declaration.md) declaración incorrectamente.

## <a name="example"></a>Ejemplo

Este error puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio 2005: ya no es válido tener un `using` declaración a un tipo anidado; debe calificar explícitamente cada referencia de tipo anidado, coloque el tipo en una n espacio ombres, o crear una definición de tipo.

El ejemplo siguiente genera C2885.

```
// C2885.cpp
namespace MyNamespace {
   class X1 {};
}

struct MyStruct {
   struct X1 {
      int i;
   };
};

int main () {
   using MyStruct::X1;   // C2885

   // OK
   using MyNamespace::X1;
   X1 myX1;

   MyStruct::X1 X12;

   typedef MyStruct::X1 abc;
   abc X13;
   X13.i = 9;
}
```

## <a name="example"></a>Ejemplo

Si usas el `using` palabra clave con un miembro de clase, C++ requiere definir ese miembro dentro de otra clase (una clase derivada).

El ejemplo siguiente genera C2885.

```
// C2885_b.cpp
// compile with: /c
class A {
public:
   int i;
};

void z() {
   using A::i;   // C2885 not in a class
}

class B : public A {
public:
   using A::i;
};
```