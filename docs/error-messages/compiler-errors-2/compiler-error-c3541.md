---
title: Error del compilador C3541
ms.date: 11/04/2016
f1_keywords:
- C3541
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
ms.openlocfilehash: 03361fa3e8d4ecb9647d354dd402a9f2b0865eb6
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037690"
---
# <a name="compiler-error-c3541"></a>Error del compilador C3541

'type': typeid no se puede aplicar a un tipo que contiene 'auto'

El [typeid](../../extensions/typeid-cpp-component-extensions.md) operador no se puede aplicar al tipo indicado porque contiene el `auto` especificador.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3541.

```
// C3541.cpp
// Compile with /Zc:auto
#include <typeinfo>
int main() {
    auto x = 123;
    typeid(x);    // OK
    typeid(auto); // C3541
    return 0;
}
```

## <a name="see-also"></a>Vea también

[auto (Palabra clave)](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (Deducir tipo de variable)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[typeid](../../extensions/typeid-cpp-component-extensions.md)