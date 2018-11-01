---
title: Error del compilador C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: 34b5cff9191814b2a16a42d9e234bab09f29c117
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490030"
---
# <a name="compiler-error-c3072"></a>Error del compilador C3072

el operador 'operator' no se puede aplicar a una instancia de una clase ref

utiliza el operador unario '`operator` ' para convertir una instancia de una clase ref en un tipo de identificador

Un tipo CLR requiere operadores CLR, no los operadores nativos (o estándares).  Para obtener más información, consulte [operador de referencia de seguimiento](../../windows/tracking-reference-operator-cpp-component-extensions.md).

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