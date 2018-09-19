---
title: Compilador advertencia (nivel 1) C4369 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4369
dev_langs:
- C++
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c8b292717168f7f6ead676528a5b7769b7c8ec4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024156"
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