---
title: "Error del compilador C2164 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2164"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2164"
ms.assetid: 55df5024-68a8-45a8-ae6c-e6dba35318a2
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C2164
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : función intrínseca no declarada  
  
 Una directiva pragma `intrinsic` está utilizando una función sin declarar \(sólo ocurre con **\/Oi**\).  O bien, se ha utilizado uno de los intrínsecos del compilador sin incluir su archivo de encabezado.  
  
 El código siguiente genera el error C2164:  
  
```  
// C2164.c  
// compile with: /c  
// processor: x86  
// Uncomment the following line to resolve.  
// #include "xmmintrin.h"  
void b(float *p) {  
   _mm_load_ss(p);   // C2164  
}  
```