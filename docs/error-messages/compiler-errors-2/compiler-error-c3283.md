---
title: Error del compilador C3283
ms.date: 11/04/2016
f1_keywords:
- C3283
helpviewer_keywords:
- C3283
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
ms.openlocfilehash: 873ab4d4b016fa392b7a2f64fdd14c3e93f2e22d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516095"
---
# <a name="compiler-error-c3283"></a>Error del compilador C3283

'type': una interfaz no puede tener un constructor de instancia

Un elemento [interface](../../windows/interface-class-cpp-component-extensions.md) de CLR no puede tener un constructor de instancia.  Se permite un constructor estático.

El ejemplo siguiente genera la advertencia C3283:

```
// C3283.cpp
// compile with: /clr
interface class I {
   I();   // C3283
};
```

Posible resolución:

```
// C3283b.cpp
// compile with: /clr /c
interface class I {
   static I(){}
};
```