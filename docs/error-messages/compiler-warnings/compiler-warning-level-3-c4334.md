---
title: Compilador advertencia (nivel 3) C4334 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4334
dev_langs:
- C++
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f26749c968c3cac18b509046633ba3d91d15a4be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292690"
---
# <a name="compiler-warning-level-3-c4334"></a>Advertencia del compilador (nivel 3) C4334
'operador': el resultado del desplazamiento de 32 bits se convierte implícitamente a 64 bits (era quería un desplazamiento de 64 bits?)  
  
 El resultado del desplazamiento de 32 bits se convierte implícitamente a 64 bits y el compilador supuso que tenía un desplazamiento de 64 bits.  Para resolver esta advertencia, use desplazamiento de 64 bits o convierta explícitamente el resultado a 64 bits.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4334.  
  
```  
// C4334.cpp  
// compile with: /W3 /c  
void SetBit(unsigned __int64 *p, int i) {  
   *p |= (1 << i);   // C4334  
   *p |= (1i64 << i);   // OK  
}  
```