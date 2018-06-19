---
title: Funciones sin prototipo | Documentos de Microsoft
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
ms.openlocfilehash: df159942832479807b2dfe2679e709292ff3f44b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380477"
---
# <a name="unprototyped-functions"></a>Funciones sin prototipo
Para las funciones sin prototipos bien definidas, el llamador pasará valores enteros como enteros y valores de punto flotante como de doble precisión. Para valores de punto flotante, tanto el registro entero y el registro de punto flotante contendrá el valor flotante en caso de que el destinatario espera el valor en los registros de enteros.  
  
```  
func1();  
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7  
   func1(2, 1.0, 7);  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Convención de llamada](../build/calling-convention.md)