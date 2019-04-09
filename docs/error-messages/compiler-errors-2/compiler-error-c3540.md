---
title: Error del compilador C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: 57e4145557272f76a890a356c79982346cd74d7e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037174"
---
# <a name="compiler-error-c3540"></a>Error del compilador C3540

'type': no se puede aplicar sizeof a un tipo que contiene 'auto'

El [sizeof](../../cpp/sizeof-operator.md) operador no se puede aplicar al tipo indicado porque contiene el `auto` especificador.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3540.

```
// C3540.cpp
// Compile with /Zc:auto
int main() {
    auto x = 123;
    sizeof(x);    // OK
    sizeof(auto); // C3540
    return 0;
}
```

## <a name="see-also"></a>Vea también

[auto (Palabra clave)](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (Deducir tipo de variable)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof (Operador)](../../cpp/sizeof-operator.md)