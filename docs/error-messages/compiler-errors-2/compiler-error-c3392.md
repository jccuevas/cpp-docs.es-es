---
title: Error del compilador C3392
ms.date: 11/04/2016
f1_keywords:
- C3392
helpviewer_keywords:
- C3392
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
ms.openlocfilehash: 4109a59f093740c9e0865cef6a31f3b09127c747
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912803"
---
# <a name="compiler-error-c3392"></a>Error del compilador C3392

'arg_tipo': argumento de tipo no válido para el parámetro genérico 'parámetro' del 'tipo_genérico' genérico, debe tener un constructor sin parámetros público.

Se crearon instancias de un tipo genérico incorrectamente. Compruebe la definición de tipo. Para obtener más información, vea [genéricos](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente C# se usa para crear un componente que contiene un tipo genérico que tiene ciertas restricciones que no se admiten al crear tipos genéricos C++en/CLI. Para obtener más información, vea [Constraints on Type Parameters](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters) (Restricciones de tipos de parámetros [Guía de programación de C#]).

```csharp
// C3392.cs
// Compile by using: csc /target:library C3392.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

Cuando el componente C3392. dll está disponible, el ejemplo siguiente genera C3392.

```cpp
// C3392_b.cpp
// Compile by using: cl /clr C3392_b.cpp
#using <C3392.dll>

ref class R { R(int) {} };
ref class N { N() {} };

value class V {};

ref class N2 { public: N2() {} };
ref class R2 { public: R2() {} };

int main () {
   GR<R^, V, N^>^ gr1;   // C3392
   GR<R^, V, N2^>^ gr1a; // OK

   GR<R^, N^, N^>^ gr3;  // C3392
   GR<R^, V, N2^>^ gr3a; // OK

   GR<R^, V, R^>^ gr4;   // C3392
   GR<R^, V, R2^>^ gr4a; // OK
}
```