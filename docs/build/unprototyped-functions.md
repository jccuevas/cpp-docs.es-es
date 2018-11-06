---
title: Funciones sin prototipo
ms.date: 11/04/2016
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
ms.openlocfilehash: 38207be6111dadc338593e55b683b88e0480e1ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633433"
---
# <a name="unprototyped-functions"></a>Funciones sin prototipo

Para las funciones prototipos no totalmente, el llamador pasará los valores enteros como enteros y valores de punto flotante como de doble precisión. Para valores de punto flotante, el registro entero y el registro de punto flotante contendrá el valor de punto flotante en caso de que el destinatario espere el valor de los registros enteros.

```
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="see-also"></a>Vea también

[Convención de llamada](../build/calling-convention.md)