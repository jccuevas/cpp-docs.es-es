---
title: Advertencia del compilador (nivel 3) C4686
ms.date: 08/27/2018
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: 5e23e6aa69fe8a59e3dfd22af7e33780c223cdd3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401610"
---
# <a name="compiler-warning-level-3-c4686"></a>Advertencia del compilador (nivel 3) C4686

> '*definido por el usuario*': posible cambio de comportamiento, cambio en el UDT devolver la convención de llamada

## <a name="remarks"></a>Comentarios

No es una especialización de plantilla de clase se define antes de usarlo en un tipo de valor devuelto. Todo lo que crea una instancia de la clase resolverá C4686; declarar una instancia o el acceso a un miembro (C\<int >:: nada) también son opciones.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

## <a name="example"></a>Ejemplo

En su lugar, intente lo siguiente:

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