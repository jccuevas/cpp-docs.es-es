---
title: Error del compilador C3391
ms.date: 11/04/2016
f1_keywords:
- C3391
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
ms.openlocfilehash: 7590ba9431892c07a32c27fdc97604c8b005fe33
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912855"
---
# <a name="compiler-error-c3391"></a>Error del compilador C3391

' type_arg ': argumento de tipo no válido para el parámetro genérico ' param ' de ' generic_type ' genérico; debe ser un tipo de valor que no acepte valores NULL

Se crearon instancias de un tipo genérico incorrectamente. Compruebe la definición de tipo. Para obtener más información, vea <xref:System.Nullable> y [genéricos](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente C# se usa para crear un componente que contiene un tipo genérico que tiene ciertas restricciones que no se admiten al crear tipos genéricos C++en/CLI. Para obtener más información, vea [Constraints on Type Parameters](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters) (Restricciones de tipos de parámetros [Guía de programación de C#]).

```csharp
// C3391.cs
// Compile by using: csc /target:library C3391.cs
// a C# program
public class GR<N>
where N : struct {}
```

Cuando el componente C3391. dll está disponible, el ejemplo siguiente genera C3391.

```cpp
// C3391_b.cpp
// Compile by using: cl /clr C3391_b.cpp
#using <C3391.dll>
using namespace System;
value class VClass {};

int main() {
   GR< Nullable<VClass> >^ a =
      gcnew GR< Nullable<VClass> >();   // C3391 can't be Nullable
   GR<VClass>^ aa = gcnew GR<VClass>(); // OK
}
```