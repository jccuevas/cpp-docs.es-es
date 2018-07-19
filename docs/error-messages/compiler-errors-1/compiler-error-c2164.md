---
title: Error del compilador C2164 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2164
dev_langs:
- C++
helpviewer_keywords:
- C2164
ms.assetid: 55df5024-68a8-45a8-ae6c-e6dba35318a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 23596fc25685adc155220de344adcd7d25827985
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171329"
---
# <a name="compiler-error-c2164"></a>Error del compilador C2164
'función': función intrínseca no declarada  
  
 Un `intrinsic` pragma usa una función sin declarar (sólo ocurre con **/Oi**). O bien, se utiliza una de las funciones intrínsecas del compilador sin incluir su archivo de encabezado.  
  
 El ejemplo siguiente genera C2164:  
  
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