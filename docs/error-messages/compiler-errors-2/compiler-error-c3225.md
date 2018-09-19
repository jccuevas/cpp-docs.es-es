---
title: Error del compilador C3225 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3225
dev_langs:
- C++
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8d8b1251b9c13a71faf771c85924a75681deab7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033256"
---
# <a name="compiler-error-c3225"></a>Error del compilador C3225

argumento de tipo genérico para 'arg' no puede ser 'tipo', debe ser un tipo de valor o tipo de identificador

El argumento de tipo genérico no era del tipo correcto.

Para más información, vea [Genéricos](../../windows/generics-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

No se puede crear una instancia de un tipo genérico con un tipo nativo. El ejemplo siguiente genera C3225.

```
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

El ejemplo siguiente crea un componente con C#. Tenga en cuenta que la restricción especifica que solo se puede crear instancias de tipo genérico con un tipo de valor.

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

## <a name="example"></a>Ejemplo

Este ejemplo utiliza C#-componente creado y se infringe la restricción que solo puede tener MyList crea una instancia con un tipo de valor distinto de <xref:System.Nullable>. El ejemplo siguiente genera C3225.

```
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