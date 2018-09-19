---
title: Funciones sin prototipo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c030bd99fc185b3c52535aecb45697672ef4c14
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717683"
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