---
title: Error del compilador C3535
ms.date: 11/04/2016
f1_keywords:
- C3535
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
ms.openlocfilehash: 6b487c0f94a00ec64e0c2178265c5a8c27544a51
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761561"
---
# <a name="compiler-error-c3535"></a>Error del compilador C3535

no se puede deducir el tipo de ' Type1 ' de ' tipo2 '

No se puede deducir el tipo de la variable declarada por la palabra clave `auto` a partir del tipo de la expresión de inicialización. Por ejemplo, este error se produce si la expresión de inicialización se evalúa como `void`, que no es un tipo.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Asegúrese de que el tipo de la expresión de inicialización no es `void`.

1. Asegúrese de que la declaración no es un puntero a un tipo fundamental. Para obtener más información, vea [tipos fundamentales](../../cpp/fundamental-types-cpp.md).

1. Asegúrese de que si la declaración es un puntero a un tipo, la expresión de inicialización es un tipo de puntero.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se produce C3535 porque la expresión de inicialización se evalúa como `void`.

```cpp
// C3535a.cpp
// Compile with /Zc:auto
void f(){}
int main()
{
   auto x = f();   //C3535
   return 0;
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se produce C3535 porque la instrucción declara la variable `x` como un puntero a un tipo deducido, pero el tipo de la expresión de inicializador es Double. Por consiguiente, el compilador no puede deducir el tipo de la variable.

```cpp
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se produce C3535 porque la variable `p` declara un puntero a un tipo deducido, pero la expresión de inicialización no es un tipo de puntero.

```cpp
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>Vea también

[Auto (palabra clave)](../../cpp/auto-keyword.md)<br/>
[Tipos fundamentales](../../cpp/fundamental-types-cpp.md)
