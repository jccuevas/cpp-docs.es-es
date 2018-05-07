---
title: Compilador advertencia (nivel 2) C4056 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4056
dev_langs:
- C++
helpviewer_keywords:
- C4056
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bf5a5855d0b4291105826679e2ae81ed6d69e5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-2-c4056"></a>Compilador C4056 de advertencia (nivel 2)
desbordamiento en aritmética de constante de punto flotante  
  
 Aritmética de constante de punto flotante genera un resultado que supera el valor máximo permitido.  
  
 Esta advertencia puede deberse a las optimizaciones del compilador realizadas durante la aritmética de constante. Se puede ignorar esta advertencia si desaparece al desactivar la optimización ([/Od](../../build/reference/od-disable-debug.md)).  
  
 El ejemplo siguiente genera C4056:  
  
```  
// C4056.cpp  
// compile with: /W2 /LD  
#pragma warning (default : 4056)  
float fp_val = 1.0e300 * 1.0e300;   // C4056  
```