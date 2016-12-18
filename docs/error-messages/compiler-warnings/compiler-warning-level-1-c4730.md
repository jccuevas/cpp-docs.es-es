---
title: "Advertencia del compilador (nivel 1) C4730 | Microsoft Docs"
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
  - "C4730"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4730"
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4730
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'main': la mezcla de \_m64 y expresiones de punto flotante podría ocasionar código incorrecto  
  
 Una función utiliza [\_\_m64](../../cpp/m64.md) y tipos **float**\/**double**.  Ya que los registros MMX y de punto flotante comparten el mismo espacio físico de registros \(no se pueden usar simultáneamente\), utilizar tipos `__m64` y **float**\/**double** en una misma función puede dar como resultado datos dañados, posiblemente causando una excepción.  
  
 Para utilizar a los tipos y los tipos de punto flotante de `__m64` en una misma función, las instrucciones que utilice uno de los tipos debe separar por **\_m\_empty\(\)** \(para MMX\) o intrínsecos de **\_m\_femms\(\)** \(para 3DNow\!\).  
  
 El código siguiente genera el error C4730:  
  
```  
// C4730.cpp  
// compile with: /W1  
// processor: x86  
#include "mmintrin.h"  
  
void func(double)  
{  
}  
  
int main(__m64 a, __m64 b)  
{  
   __m64 m;  
   double f;  
   f = 1.0;  
   m = _m_paddb(a, b);  
   // uncomment the next line to resolve C4730  
   // _m_empty();  
   func(f * 3.0);   // C4730  
}  
```