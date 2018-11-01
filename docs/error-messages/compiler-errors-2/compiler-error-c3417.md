---
title: Error del compilador C3417
ms.date: 11/04/2016
f1_keywords:
- C3417
helpviewer_keywords:
- C3417
ms.assetid: 3e7869ea-8948-42fb-ba30-6ccafe499c35
ms.openlocfilehash: 574af940f17c1a79472d6d20d63c9ff74d4c411e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615778"
---
# <a name="compiler-error-c3417"></a>Error del compilador C3417

'member': tipos de valor no pueden contener funciones miembro especiales definidas por el usuario

Tipos de valor no pueden contener funciones como un constructor de instancia predeterminado, un destructor o un constructor de copias.

El ejemplo siguiente genera C3517:

```
// C3417.cpp
// compile with: /clr /c
value class VC {
   VC(){}   // C3417

   // OK
   static VC(){}
   VC(int i){}
};
```