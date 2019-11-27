---
title: Advertencia del compilador (nivel 3) C4522
ms.date: 11/04/2016
f1_keywords:
- C4522
helpviewer_keywords:
- C4522
ms.assetid: 7065dc27-0b6c-4e68-a345-c51cdb99a20b
ms.openlocfilehash: 84f4785c670c4cc5c167c18b9f15c2417b61df34
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188968"
---
# <a name="compiler-warning-level-3-c4522"></a>Advertencia del compilador (nivel 3) C4522

' Class ': se especificaron varios operadores de asignación

La clase tiene varios operadores de asignación de un único tipo. Esta advertencia es informativa; se puede llamar a los constructores en el programa.

Use la pragma [Warning](../../preprocessor/warning.md) para suprimir esta advertencia.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4522.

```cpp
// C4522.cpp
// compile with: /EHsc /W3
#include <iostream>

using namespace std;
class A {
public:
   A& operator=( A & o ) { cout << "A&" << endl; return *this; }
   A& operator=( const A &co ) { cout << "const A&" << endl; return *this; }   // C4522
};

int main() {
   A o1, o2;
   o2 = o1;
   const A o3;
   o1 = o3;
}
```