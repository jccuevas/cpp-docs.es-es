---
title: Advertencia del compilador (nivel 1) C4817
ms.date: 11/04/2016
f1_keywords:
- C4817
helpviewer_keywords:
- C4817
ms.assetid: a68f5486-6940-4934-9f93-bfd4d71f92a9
ms.openlocfilehash: bb6eb8899efdab3cae39f77079f7eed72344acc1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406423"
---
# <a name="compiler-warning-level-1-c4817"></a>Advertencia del compilador (nivel 1) C4817

'meber': uso no válido de '.' para obtener acceso a este miembro; el compilador lo reemplazó por '->'

Se usó el operador de acceso de miembro equivocado.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4817:

```
// C4817.cpp
// compile with: /clr /W1
using namespace System;
int main() {
   array<Int32> ^ a = gcnew array<Int32>(100);
   Console::WriteLine( a.Length );   // C4817
   Console::WriteLine( a->Length );   // OK
}
```
