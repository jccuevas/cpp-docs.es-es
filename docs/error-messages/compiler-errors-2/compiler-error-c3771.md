---
title: Error del compilador C3771
ms.date: 11/04/2016
f1_keywords:
- C3771
helpviewer_keywords:
- C3771
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
ms.openlocfilehash: 6c29ad6007d33c43ae1e4758ae05caa9109053e3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165735"
---
# <a name="compiler-error-c3771"></a>Error del compilador C3771

"identifier": no se puede encontrar ninguna declaración friend en el ámbito del espacio de nombres más próximo

La declaración de la plantilla de clase de la plantilla especificada *identifier* no se encuentra en el espacio de nombres actual.

### <a name="to-correct-this-error"></a>Para corregir este error

- Asegúrese de que la declaración de la plantilla de clase del identificador de plantilla está definida en el espacio de nombres actual o que el identificador de plantilla sea un nombre completo.

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se declara una función y plantilla de clase en el espacio de nombres `NA`, pero se intenta declarar una plantilla de función friend en el espacio de nombres `NB`.

```cpp
// C3771.cpp
// compile with: /c

namespace NA {
template<class T> class A {
    void aFunction(T t) {};
    };
}
// using namespace NA;
namespace NB {
    class X {
        template<class T> friend void A<T>::aFunction(T); // C3771
// try the following line instead
//      template<class T> friend void NA::A<T>::aFunction(T);
// or try "using namespace NA;" instead.
    };
}
```

## <a name="see-also"></a>Consulte también

[Templates](../../cpp/templates-cpp.md) (Plantillas [C++])
