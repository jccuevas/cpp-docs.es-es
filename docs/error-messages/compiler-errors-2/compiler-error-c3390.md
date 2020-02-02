---
title: Error del compilador C3390
ms.date: 11/04/2016
f1_keywords:
- C3390
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
ms.openlocfilehash: c624d3b0379d057b0ed566deffc2a0efcc324f88
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912871"
---
# <a name="compiler-error-c3390"></a>Error del compilador C3390

'type_arg': argumento de tipo no válido para el parámetro genérico 'param' de 'generic_type' genérico; debe ser un tipo de referencia

Se crearon instancias de un tipo genérico incorrectamente.  Compruebe la definición de tipo.  Para obtener más información, consulte [Genéricos](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

En el primer ejemplo C# se usa para crear un componente que contiene un tipo genérico que tiene ciertas restricciones que no se admiten al crear tipos genéricos C++en/CLR. Para obtener más información, vea [Constraints on Type Parameters](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters) (Restricciones de tipos de parámetros [Guía de programación de C#]).

```csharp
// C3390.cs
// Compile by using: csc /target:library C3390.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

Cuando el componente C3390. dll está disponible, el ejemplo siguiente genera C3390.

```cpp
// C3390_b.cpp
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>
ref class R { R(int) {} };
value class V {};
ref struct N { N() {} };

int main () {
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type
   GR<R^, V, N^>^ gr2b; // OK
}
```