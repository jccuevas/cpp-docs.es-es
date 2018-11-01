---
title: Error del compilador C3063
ms.date: 11/04/2016
f1_keywords:
- C3063
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
ms.openlocfilehash: 9e53d9fe273a392695212df6dbeb679822a39068
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485552"
---
# <a name="compiler-error-c3063"></a>Error del compilador C3063

el operador 'operator': todos los operandos deben tener el mismo tipo de enumeración

Cuando se utilizan operadores sobre los enumeradores, ambos operandos deben ser del tipo de enumeración. Para obtener más información, consulte [Cómo: definir y usar enumeraciones en C++ / c++ / CLI](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3063 y muestra cómo corregirlo:

```
// C3063.cpp
// compile with: /clr
enum class E { a, b } e, mask;
int main() {
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)

   if ( ( e & mask ) != E() )   // OK
      ;
}
```