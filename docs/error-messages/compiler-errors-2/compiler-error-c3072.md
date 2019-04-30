---
title: Error del compilador C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: 2b76fa91d739e9cc89251aaf56aa9b196e62a68d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406735"
---
# <a name="compiler-error-c3072"></a>Error del compilador C3072

el operador 'operator' no se puede aplicar a una instancia de una clase ref

utiliza el operador unario '`operator` ' para convertir una instancia de una clase ref en un tipo de identificador

Un tipo CLR requiere operadores CLR, no los operadores nativos (o estándares).  Para obtener más información, consulte [operador de referencia de seguimiento](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3072.

```
// C3072.cpp
// compile with: /clr
ref class R {};

int main() {
   R r1;
   R^ r2 = &r1;   // C3072
   R^ r3 = %r1;   // OK
}
```