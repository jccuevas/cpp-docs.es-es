---
title: Advertencia del compilador (nivel 3) C4521
ms.date: 11/04/2016
f1_keywords:
- C4521
helpviewer_keywords:
- C4521
ms.assetid: 057d770c-ebcf-44cd-b943-1b1bb1ceaa8c
ms.openlocfilehash: 362fd3c14037fa62ab73c928a45eaf7808de66bc
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189359"
---
# <a name="compiler-warning-level-3-c4521"></a>Advertencia del compilador (nivel 3) C4521

' Class ': se especificaron varios constructores de copias

La clase tiene varios constructores de copia de un único tipo. Esta advertencia es informativa; se puede llamar a los constructores en el programa.

Use la pragma [Warning](../../preprocessor/warning.md) para suprimir esta advertencia.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4521.

```cpp
// C4521.cpp
// compile with: /EHsc /W3
#include <iostream>

using namespace std;
class A {
public:
   A() { cout << "A's default constructor" << endl; }
   A( A &o ) { cout << "A&" << endl; }
   A( const A &co ) { cout << "const A&" << endl; }   // C4521
};

int main() {
   A o1;         // Calls default constructor.
   A o2( o1 );   // Calls A( A& ).
   const A o3;   // Calls default constructor.
   A o4( o3 );   // Calls A( const A& ).
}
```