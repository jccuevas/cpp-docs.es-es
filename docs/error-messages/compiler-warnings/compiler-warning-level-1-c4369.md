---
title: Advertencia del compilador (nivel 1) C4369
ms.date: 11/04/2016
f1_keywords:
- C4369
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
ms.openlocfilehash: b374b67fa3319be35490358d7664bcb45bc640db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207035"
---
# <a name="compiler-warning-level-1-c4369"></a>Advertencia del compilador (nivel 1) C4369

'enumerador': el valor de enumerador 'valor' no se puede representar como 'type', el valor es 'new_value'

Un enumerador se calculó para que sea mayor que el valor máximo para el tipo subyacente especificado.  Esto provocó un desbordamiento y el compilador ajusta el valor del enumerador para el valor más bajo posible para el tipo.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4369.

```
// C4369.cpp
// compile with: /W1
int main() {
   enum Color: char { red = 0x7e, green, blue };   // C4369
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK
}
```