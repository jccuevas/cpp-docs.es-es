---
title: Error del compilador C3068
ms.date: 11/04/2016
f1_keywords:
- C3068
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
ms.openlocfilehash: 9e20333a4fc18219f7f2514f3aefe73b81f284a6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759495"
---
# <a name="compiler-error-c3068"></a>Error del compilador C3068

' function ': una función ' naked ' no puede contener objetos que requieran el desenredo C++ si se produjo una excepción

El compilador no pudo realizar el desenredo de la pila en una función [naked](../../cpp/naked-cpp.md) que produjo una excepción porque se ha creado un objeto temporal C++ en la función y se ha especificado el control de excepciones ([/EHsc](../../build/reference/eh-exception-handling-model.md)).

Para resolver este error, realice al menos uno de los siguientes elementos:

- No compilar con/EHsc.

- No marque la función como `naked`.

- No cree un objeto temporal en la función.

Si una función crea un objeto temporal en la pila, si la función produce una excepción y si C++ el control de excepciones está habilitado, el compilador limpiará la pila si se produce una excepción.

Cuando se inicia una excepción, el código generado por el compilador, denominado prólogo y epílogo y que no están presentes en una función Naked, se ejecuta para una función.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3068:

```cpp
// C3068.cpp
// compile with: /EHsc
// processor: x86
class A {
public:
   A(){}
   ~A(){}
};

void b(A){}

__declspec(naked) void c() {
   b(A());   // C3068
};
```
