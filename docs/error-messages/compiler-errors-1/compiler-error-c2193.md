---
title: Error del compilador C2193 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2193
dev_langs:
- C++
helpviewer_keywords:
- C2193
ms.assetid: 9813e853-d581-4f51-bb75-4e242298a844
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: e59b7e3ab659ee7760254680e51db9e2d4ca35d7
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2193"></a>Error del compilador C2193
'identificador': ya se encuentran en un segmento  
  
 Se ha colocado una función en dos segmentos diferentes usando `alloc_text` y `code_seg` pragma (directivas).  
  
 El ejemplo siguiente genera C2193:  
  
```  
// C2193.cpp  
// compile with: /c  
extern "C" void MYFUNCTION();  
#pragma alloc_text(MYCODE, MYFUNCTION)  
#pragma code_seg("MYCODE2")  
extern "C" void MYFUNCTION() {}   // C2193  
extern "C" void MYFUNCTION2() {}  
```
