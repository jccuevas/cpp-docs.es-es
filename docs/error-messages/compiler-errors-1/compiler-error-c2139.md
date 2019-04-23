---
title: Error del compilador C2139
ms.date: 11/04/2016
f1_keywords:
- C2139
helpviewer_keywords:
- C2139
ms.assetid: 31e047c0-5bf9-46c2-b6de-b627ea6a5768
ms.openlocfilehash: 15813216399c0f00fea036cd95443235e7acf4c3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776806"
---
# <a name="compiler-error-c2139"></a>Error del compilador C2139

'type': no se permite una clase no definida como argumento para el rasgo de tipo intrínseco 'rasgo'

Se pasó un argumento no válido a un rasgo de tipo.

Para obtener más información, consulte [compatibilidad de compilador para Type Traits](../../extensions/compiler-support-for-type-traits-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C2139.

```
// C2139.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T>
struct is_polymorphic {
   static const bool value = __is_polymorphic(T);
};

class C;
class D {};

class E {
public:
   virtual void Test() {}
};

int main() {
   cout << is_polymorphic<C>::value << endl;   // C2139
   cout << is_polymorphic<D>::value << endl;   // OK
   cout << is_polymorphic<E>::value << endl;   // OK
}
```