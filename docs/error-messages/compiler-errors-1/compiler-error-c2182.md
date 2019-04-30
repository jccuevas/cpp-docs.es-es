---
title: Error del compilador C2182
ms.date: 11/04/2016
f1_keywords:
- C2182
helpviewer_keywords:
- C2182
ms.assetid: dfd8d47d-9606-496e-bd96-4bf41ba1f857
ms.openlocfilehash: 3c33e722143c15c566d96226429adbb8868b34ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385984"
---
# <a name="compiler-error-c2182"></a>Error del compilador C2182

'identifier': uso no válido del tipo 'void'

Una variable se declara de tipo `void`.

El ejemplo siguiente genera la advertencia C2182:

```
// C2182.cpp
// compile with: /c
int main() {
   int i = 10;
   void &ir = i;   // C2182 cannot have a reference to type void
   int &ir = i;   // OK
}
```