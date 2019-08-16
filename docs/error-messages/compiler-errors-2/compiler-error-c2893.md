---
title: Error del compilador C2893
ms.date: 11/04/2016
f1_keywords:
- C2893
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
ms.openlocfilehash: f1fad1ad18af54945ef32dadaac50a6de4dbd62f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366386"
---
# <a name="compiler-error-c2893"></a>Error del compilador C2893

No se pudo especializar la plantilla de función 'nombre de plantilla'

El compilador no se pudo especializar una plantilla de función. Puede haber varias causas para este error.

En general, la manera de solucionar el error 2893 es revisar la firma de la función y asegúrese de que puede crear una instancia de cada tipo.

## <a name="example"></a>Ejemplo

C2893 se produce porque `f`del parámetro de plantilla `T` se deduce que `std::map<int,int>`, pero `std::map<int,int>` no tiene ningún miembro `data_type` (`T::data_type` no se pueden crear instancias con `T = std::map<int,int>`.). El ejemplo siguiente genera C2893.

```
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