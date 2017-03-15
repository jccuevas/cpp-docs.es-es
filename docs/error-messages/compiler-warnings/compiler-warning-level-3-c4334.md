---
title: "Advertencia del compilador (nivel 3) C4334 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4334"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4334"
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 3) C4334
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador' : el resultado del desplazamiento de 32 bits se convirtió implícitamente en 64 bits \(¿iba a ser un desplazamiento de 64 bits?\)  
  
 El resultado del desplazamiento de 32 bits se convirtió implícitamente en 64 bits y el compilador supuso que el desplazamiento era de 64 bits.  Para resolver esta advertencia, use desplazamiento de 64 bits o convierta explícitamente el resultado a 64 bits.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4334.  
  
```  
// C4334.cpp  
// compile with: /W3 /c  
void SetBit(unsigned __int64 *p, int i) {  
   *p |= (1 << i);   // C4334  
   *p |= (1i64 << i);   // OK  
}  
```