---
title: Error del compilador C3768
ms.date: 11/04/2016
f1_keywords:
- C3768
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
ms.openlocfilehash: 534be9e3873276313335ca921264be92c9259b93
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165748"
---
# <a name="compiler-error-c3768"></a>Error del compilador C3768

> no se puede adquirir la dirección de una función vararg virtual en código administrado puro

## <a name="remarks"></a>Observaciones

La opción del compilador **/clr: Pure** ha quedado en desuso en visual Studio 2015 y no se admite en visual Studio 2017.

Al compilar con **/clr: Pure**, no se puede tomar la dirección de una función de `vararg` virtual.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3768:

```cpp
// C3768.cpp
// compile with: /clr:pure
struct A
{
   virtual void f(...);
};

int main()
{
   &(A::f);   // C3768
}
```
