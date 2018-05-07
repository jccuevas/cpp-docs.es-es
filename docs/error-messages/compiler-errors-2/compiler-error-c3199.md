---
title: C3199 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3199
dev_langs:
- C++
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cddad2218e81603f59cad51e3a684303e144171e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3199"></a>C3199 de Error del compilador
uso no válido de pragmas de punto flotante: excepciones no se admiten en el modo no es preciso  
  
 El [float_control](../../preprocessor/float-control.md) pragma se utiliza para especificar el modelo de excepciones de punto flotante en una [/FP](../../build/reference/fp-specify-floating-point-behavior.md) valor distinto de **/fp: precisa**.  
  
 El ejemplo siguiente genera C3199:  
  
```  
// C3199.cpp  
// compile with: /fp:fast  
#pragma float_control(except, on)   // C3199  
```