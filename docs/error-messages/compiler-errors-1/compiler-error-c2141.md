---
title: "Error del compilador C2141 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2141"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2141"
ms.assetid: 10cf770f-0500-4220-ac90-a863b7ea5fe6
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2141
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

desbordamiento del tamaño de la matriz  
  
 Hay una matriz que supera el límite de 2 GB.  Deberá reducir su tamaño.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2141.  
  
```  
// C2141.cpp  
// processor: IPF  
class A {  
   short m_n;  
};  
  
int main()  
{  
   A* pA = (A*)(-1);  
   pA = new A[0x8000000000000001];   // C2141  
  
   A* pA2 = (A*)(-1);  
   pA2 = new A[0x80000000000000F];   // OK  
}  
```