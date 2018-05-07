---
title: Error del compilador C2881 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2881
dev_langs:
- C++
helpviewer_keywords:
- C2881
ms.assetid: b49c63c2-b064-4d4b-a75e-ddd2af947522
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68be8efee689caab28c420d745bdfb59fb25f641
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2881"></a>Error del compilador C2881
'namespace1': ya se utiliza como un alias de espacio de nombres '2'  
  
 No se puede usar el mismo nombre como alias para dos espacios de nombres.  
  
 El ejemplo siguiente genera C2881:  
  
```  
// C2881.cpp  
// compile with: /c  
namespace A {  
   int k;  
}  
  
namespace B {  
   int i;  
}  
  
namespace C = A;  
namespace C = B;   // C2881 C is already an alias for A  
```