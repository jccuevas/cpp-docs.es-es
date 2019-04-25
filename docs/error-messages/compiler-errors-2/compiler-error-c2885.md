---
title: Error del compilador C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: 8174faed09bdffbdc6974390cceb7c17661eab4b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388779"
---
# <a name="compiler-error-c2885"></a>Error del compilador C2885

'Class:: identifier': no es una declaración using válida en el ámbito de no clase

Ha utilizado un [mediante](../../cpp/using-declaration.md) declaración incorrectamente.

## <a name="example"></a>Ejemplo

Este error puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: ya no es válido tener un `using` declaración a un tipo anidado; debe calificar explícitamente cada referencia de tipo anidado, coloque el tipo en un nombre espacio o crear una definición de tipo.

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