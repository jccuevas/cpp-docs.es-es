---
title: Advertencia del compilador (nivel 3) C4686
ms.date: 08/27/2018
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: a8eae1ddeb875d267b82c67e989cb41e8c9b2afb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185456"
---
# <a name="compiler-warning-level-3-c4686"></a>Advertencia del compilador (nivel 3) C4686

> '*tipo definido por el usuario*': posible cambio de comportamiento, cambio en la Convención de llamada de devolución UDT

## <a name="remarks"></a>Observaciones

Una especialización de plantilla de clase no se definió antes de usarse en un tipo de valor devuelto. Todo lo que cree una instancia de la clase resolverá C4686; declarar una instancia o tener acceso a un miembro (C\<int >:: todo) también son opciones.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

## <a name="example"></a>Ejemplo

Pruebe lo siguiente en su lugar:

```cpp
// C4686.cpp
// compile with: /W3
#pragma warning (default : 4686)
template <class T>
class C;

template <class T>
C<T> f(T);

template <class T>
class C {};

int main() {
   f(1);   // C4686
}

template <class T>
C<T> f(T) {
   return C<int>();
}
```
