---
title: Error del compilador C2341 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2341
dev_langs: C++
helpviewer_keywords: C2341
ms.assetid: aa2a7da5-e1c8-4225-9939-5bdc50158f31
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 03ceeb7f34ca7aca58151174c327161b18f3678f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2341"></a>Error del compilador C2341
'section name': se debe definir el segmento utilizando #pragma data_seg, code_seg o sección anterior para usar  
  
 Un [asignar](../../cpp/allocate.md) instrucción hace referencia a un segmento aún no se ha definido por [code_seg](../../preprocessor/code-seg.md), [data_seg](../../preprocessor/data-seg.md), o [sección](../../preprocessor/section.md) pragma (directivas).  
  
 El ejemplo siguiente genera C2341:  
  
```  
// C2341.cpp  
// compile with: /c  
__declspec(allocate(".test"))   // C2341  
int j = 1;  
```  
  
 Posible resolución:  
  
```  
// C2341b.cpp  
// compile with: /c  
#pragma data_seg(".test")  
__declspec(allocate(".test"))  
int j = 1;  
```