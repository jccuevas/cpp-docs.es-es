---
title: Funciones sin prototipo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 574c4564394e251dde9345d3658304019dae838d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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