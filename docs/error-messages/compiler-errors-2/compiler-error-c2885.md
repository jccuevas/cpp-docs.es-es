---
title: Error del compilador C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: e60f3fff2ef61f4d6374072c05a2ad3e64a57031
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760933"
---
# <a name="compiler-error-c2885"></a>Error del compilador C2885

' Class:: Identifier ': no es una declaración Using válida en un ámbito que no es de clase

Usó una declaración [using](../../cpp/using-declaration.md) de forma incorrecta.

## <a name="example"></a>Ejemplo

Este error se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio 2005: ya no es válido tener una declaración de `using` a un tipo anidado; debe calificar explícitamente cada referencia que realice al tipo anidado, colocar el tipo en un espacio de nombres o crear una definición de tipos.

En el ejemplo siguiente se genera C2885.

```cpp
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

Si usa la palabra clave `using` con un miembro de clase C++ , requiere que defina ese miembro dentro de otra clase (una clase derivada).

En el ejemplo siguiente se genera C2885.

```cpp
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
