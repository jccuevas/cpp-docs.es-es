---
title: Error del compilador C3532
ms.date: 11/04/2016
f1_keywords:
- C3532
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
ms.openlocfilehash: 2ef5eb3c2bedd9defbd0b80e6d8c5c8912fcf16d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761938"
---
# <a name="compiler-error-c3532"></a>Error del compilador C3532

' tipo ': uso incorrecto de ' auto '

El tipo indicado no se puede declarar con la palabra clave `auto`. Por ejemplo, no puede utilizar la palabra clave `auto` para declarar una matriz o un tipo de valor devuelto de método.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Asegúrese de que la expresión de inicialización produce un tipo válido.

1. Asegúrese de que no declara una matriz o un tipo de valor devuelto de método.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se produce C3532 porque la palabra clave `auto` no puede declarar un tipo de valor devuelto de método.

```cpp
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se produce C3532 porque la palabra clave `auto` no puede declarar una matriz.

```cpp
// C3532b.cpp
// Compile with /Zc:auto
int main()
{
   int x[5];
   auto a[5];            // C3532
   auto b[1][2];         // C3532
   auto y[5] = x;        // C3532
   auto z[] = {1, 2, 3}; // C3532
   auto w[] = x;         // C3532
   return 0;
}
```

## <a name="see-also"></a>Vea también

[Auto (palabra clave)](../../cpp/auto-keyword.md)
