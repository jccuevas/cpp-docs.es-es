---
title: Error del compilador C3225
ms.date: 11/04/2016
f1_keywords:
- C3225
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
ms.openlocfilehash: 1caa1e7ce787ffc14e615c946b5d670c75e0332a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757623"
---
# <a name="compiler-error-c3225"></a>Error del compilador C3225

el argumento de tipo genérico para ' arg ' no puede ser ' type '; debe ser un tipo de valor o un tipo de identificador

El argumento de tipo genérico no era del tipo correcto.

Para más información, vea [Genéricos](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

No se puede crear una instancia de un tipo genérico con un tipo nativo. En el ejemplo siguiente se genera C3225.

```cpp
// C3225.cpp
// compile with: /clr
class A {};

ref class B {};

generic <class T>
ref class C {};

int main() {
   C<A>^ c = gcnew C<A>;   // C3225
   C<B^>^ c2 = gcnew C<B^>;   // OK
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un C#componente con. Observe que la restricción especifica que solo se pueden crear instancias del tipo genérico con un tipo de valor.

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

## <a name="example"></a>Ejemplo

En este ejemplo se usa C#el componente-creado y se infringe la restricción de que solo se pueden crear instancias de la lista con un tipo de valor distinto de <xref:System.Nullable>. En el ejemplo siguiente se genera C3225.

```cpp
// C3225_c.cpp
// compile with: /clr
#using "C3225_b.dll"
ref class A {};
value class B {};
int main() {
   MyList<A> x;   // C3225
   MyList<B> y;   // OK
}
```
