---
title: Error del compilador C3068
ms.date: 11/04/2016
f1_keywords:
- C3068
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
ms.openlocfilehash: 4790c9caafd28722f3631104cfe5cfc762cf6426
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575479"
---
# <a name="compiler-error-c3068"></a>Error del compilador C3068

'function': una función 'naked' no puede contener objetos que requerirían desenredo si se ha producido una excepción de C++

El compilador no pudo realizar un desenredo de pila en un [naked](../../cpp/naked-cpp.md) función que produjo una excepción porque se creó un objeto temporal en la función y el control de excepciones de C++ ([/EHsc](../../build/reference/eh-exception-handling-model.md)) se ha especificado.

Para resolver este error, realice al menos uno de los siguientes:

- No se compilan con/EHsc.

- No marque la función como `naked`.

- No cree un objeto temporal en la función.

Si una función crea un objeto temporal en la pila, si la función produce una excepción, y si está habilitado el control de excepciones de C++, el compilador limpiará la pila si se produce una excepción.

Cuando se produce una excepción, compilador genera código, llamado el prólogo y epílogo y que no están presentes en una función naked, se ejecuta en una función.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3068:

```
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