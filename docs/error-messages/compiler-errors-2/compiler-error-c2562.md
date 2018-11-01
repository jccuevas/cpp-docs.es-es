---
title: Error del compilador C2562
ms.date: 11/04/2016
f1_keywords:
- C2562
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
ms.openlocfilehash: c665c4ed82fefaf0ee724defb8c205f86fc06dd0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435314"
---
# <a name="compiler-error-c2562"></a>Error del compilador C2562

'identifier': función 'void' que devuelve un valor

La función se declara como `void` pero devuelve un valor.

Este error puede deberse a un prototipo de función incorrecto.

Este error puede corregirse si se especifica el tipo de valor devuelto en la declaración de función.

El ejemplo siguiente genera C2562:

```
// C2562.cpp
// compile with: /c
void testfunc() {
   int i;
   return i;   // C2562 delete the return to resolve
}
```