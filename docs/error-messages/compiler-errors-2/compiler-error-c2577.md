---
title: Error del compilador C2577
ms.date: 11/04/2016
f1_keywords:
- C2577
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
ms.openlocfilehash: acb42f9b792b3908a153737bcec93a449b656147
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755452"
---
# <a name="compiler-error-c2577"></a>Error del compilador C2577

' Member ': el destructor/finalizador no puede tener un tipo de valor devuelto

Un destructor o finalizador no puede devolver un valor de `void` o de cualquier otro tipo. Quite la instrucción `return` de la definición del destructor.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2577.

```cpp
// C2577.cpp
// compile with: /c
class A {
public:
   A() {}
   ~A(){
      return 0;   // C2577
   }
};
```
