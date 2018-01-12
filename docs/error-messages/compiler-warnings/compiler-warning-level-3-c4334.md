---
title: Compilador advertencia (nivel 3) C4334 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4334
dev_langs: C++
helpviewer_keywords: C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7218caa399aec0bd1b9755fb6d0942991732121e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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