---
title: Error del compilador C3390
ms.date: 11/04/2016
f1_keywords:
- C3390
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
ms.openlocfilehash: 3f1149d4584a0ea3d0061a3ec4e2b77830603ef2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778740"
---
# <a name="compiler-error-c3390"></a>Error del compilador C3390

'type_arg': argumento de tipo no válido para el parámetro genérico 'param' de 'generic_type' genérico; debe ser un tipo de referencia

Se crearon instancias de un tipo genérico incorrectamente.  Compruebe la definición de tipo.  Para más información, vea [Genéricos](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El primer ejemplo utiliza C# para crear un componente que contiene un tipo genérico que tiene ciertas restricciones que no se admiten al crear tipos genéricos en C / c++ / CLR. Para obtener más información, vea [Restricciones de tipos de parámetros](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```cs
// C3390.cs
// Compile by using: csc /target:library C3390.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

Cuando el componente C3390.dll está disponible, el ejemplo siguiente genera la advertencia C3390.

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