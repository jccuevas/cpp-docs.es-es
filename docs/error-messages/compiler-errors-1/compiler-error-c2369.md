---
title: Error del compilador C2369 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2369
dev_langs:
- C++
helpviewer_keywords:
- C2369
ms.assetid: 2a3933f6-2313-40ff-800f-921b296fdbbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b1c97f8451e6807e6b78148a7027c37ccc967bd4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2369"></a>Error del compilador C2369
'matriz': nueva definición; subíndices distintos  
  
 La matriz se declaró con un subíndice diferente.  
  
 El ejemplo siguiente genera la advertencia C2369:  
  
```  
// C2369.cpp  
// compile with: /c  
int a[10];  
int a[20];   // C2369  
int b[20];   // OK  
```