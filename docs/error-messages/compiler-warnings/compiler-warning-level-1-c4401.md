---
title: Advertencia del compilador (nivel 1) C4401
ms.date: 11/04/2016
f1_keywords:
- C4401
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
ms.openlocfilehash: fe08509a05eed00f7e7d492e723e873d05e451ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162665"
---
# <a name="compiler-warning-level-1-c4401"></a>Advertencia del compilador (nivel 1) C4401

' bits ': el miembro es un campo de bits

El código de ensamblado alineado intenta tener acceso a un miembro de campo de bits. El ensamblado alineado no puede tener acceso a los miembros de campo de bits, por lo que se usa el último límite de empaquetado antes del miembro de campo de bits.

Para evitar esta advertencia, convierta el campo de bits a un tipo adecuado antes de hacer la referencia en el código de ensamblado alineado. En el ejemplo siguiente se genera C4401:

```cpp
// C4401.cpp
// compile with: /W1
// processor: x86
typedef struct bitfield {
   signed bit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bf.bit = 0;
   __asm {
      mov bf.bit,0;   // C4401
   }

   /* use the following __asm block to resolve the warning
   int i = (int)bf.bit;
   __asm {
      mov i,0;
   }
   */
}
```
