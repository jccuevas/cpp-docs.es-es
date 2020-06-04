---
title: Advertencia del compilador (nivel 1) C4369
ms.date: 11/04/2016
f1_keywords:
- C4369
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
ms.openlocfilehash: b0d99792e3e0ea372c8629319553dd9a59ad4b47
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187068"
---
# <a name="compiler-warning-level-1-c4369"></a>Advertencia del compilador (nivel 1) C4369

' enumerador ': el valor del enumerador ' valor ' no se puede representar como ' tipo ', el valor es ' new_value '

Un enumerador se calculó como mayor que el valor más alto para el tipo subyacente especificado.  Esto produjo un desbordamiento y el compilador ajustó el valor del enumerador al valor más bajo posible para el tipo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4369.

```cpp
// C4369.cpp
// compile with: /W1
int main() {
   enum Color: char { red = 0x7e, green, blue };   // C4369
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK
}
```
