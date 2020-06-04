---
title: Error del compilador C2893
ms.date: 11/04/2016
f1_keywords:
- C2893
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
ms.openlocfilehash: ca603eb94d5d528a7fed15e0320e1f5d88bf0629
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760881"
---
# <a name="compiler-error-c2893"></a>Error del compilador C2893

No se pudo especializar la plantilla de función ' nombre de plantilla '

El compilador no pudo especializar una plantilla de función. Puede haber muchas causas para este error.

En general, la manera de resolver un error C2893 es revisar la firma de la función y asegurarse de que puede crear instancias de cada tipo.

## <a name="example"></a>Ejemplo

C2893 se produce porque `f`parámetro de plantilla de `T` se deduce que se va a `std::map<int,int>`, pero `std::map<int,int>` no tiene `data_type` de miembro (no se pueden crear instancias de`T::data_type` con `T = std::map<int,int>`). En el ejemplo siguiente se genera C2893.

```cpp
// C2893.cpp
// compile with: /c /EHsc
#include<map>
using namespace std;
class MyClass {};

template<class T>
inline typename T::data_type
// try the following line instead
// inline typename  T::mapped_type
f(T const& p1, MyClass const& p2);

template<class T>
void bar(T const& p1) {
    MyClass r;
    f(p1,r);   // C2893
}

int main() {
   map<int,int> m;
   bar(m);
}
```
