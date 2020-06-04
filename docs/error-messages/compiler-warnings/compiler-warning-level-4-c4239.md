---
title: Advertencia del compilador (nivel 4) C4239
ms.date: 11/04/2016
f1_keywords:
- C4239
helpviewer_keywords:
- C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
ms.openlocfilehash: a882fa7f78f68cb2400e4924a9ba2f17e6ee7003
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991460"
---
# <a name="compiler-warning-level-4-c4239"></a>Advertencia del compilador (nivel 4) C4239

se ha utilizado una extensión no estándar: ' token ': conversión de ' tipo ' a ' tipo '

Esta conversión de tipos no está permitida C++ por el estándar, pero se permite aquí como extensión. Esta advertencia siempre va seguida de al menos una línea de explicación que describe la regla de idioma que se infringe.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4239.

```cpp
// C4239.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

void func(void) {
   C & rC = C();   // C4239
   const C & rC2 = C();   // OK
   rC2;
}
```

## <a name="example"></a>Ejemplo

La conversión de un tipo entero a un tipo de enumeración no está permitida.

En el ejemplo siguiente se genera C4239.

```cpp
// C4239b.cpp
// compile with: /W4 /c
enum E { value };
struct S {
   E e : 2;
} s = { 5 };   // C4239
// try the following line instead
// } s = { (E)5 };
```
