---
title: Error del compilador C3699
ms.date: 11/04/2016
f1_keywords:
- C3699
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
ms.openlocfilehash: ec902266550e591623894823e6336bd2436bfbd5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758039"
---
# <a name="compiler-error-c3699"></a>Error del compilador C3699

' Operator ': no se puede usar este direccionamiento indirecto en el tipo ' type '

Se intentó usar el direccionamiento indirecto no permitido en `type`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3699.

```cpp
// C3699.cpp
// compile with: /clr /c
using namespace System;
int main() {
   String * s;   // C3699
   // try the following line instead
   // String ^ s2;
}
```

## <a name="example"></a>Ejemplo

Una propiedad trivial no puede tener un tipo de referencia. Vea [property](../../extensions/property-cpp-component-extensions.md) para obtener más información. En el ejemplo siguiente se genera C3699.

```cpp
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

## <a name="example"></a>Ejemplo

El equivalente de una sintaxis de "puntero a puntero" es un identificador de una referencia de seguimiento. En el ejemplo siguiente se genera C3699.

```cpp
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```
