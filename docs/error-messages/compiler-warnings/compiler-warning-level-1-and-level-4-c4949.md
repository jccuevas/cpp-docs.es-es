---
title: Compilador (niveles 1 y 4) C4949 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4949
dev_langs:
- C++
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 241e0295b16ae350cec213bf25b93f7ad72a0808
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>Advertencia del compilador (niveles 1 y 4) C4949
pragma (directivas) 'administrado' y 'unmanaged' es significativos cuando se compila con ' / clr [: opción]'  
  
 El compilador omite la [administrada](../../preprocessor/managed-unmanaged.md) y no administrada de pragma (directivas) si no se compila el código fuente con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). La advertencia es informativa.  
  
 El ejemplo siguiente genera C4949:  
  
```  
// C4949.cpp  
// compile with: /LD /W1  
#pragma managed   // C4949  
```  
  
 Cuando **#pragma unmanaged** se usa sin **/CLR**, C4949 es una advertencia de nivel 4.  
  
 El ejemplo siguiente genera C4949:  
  
```  
// C4949b.cpp  
// compile with: /LD /W4  
#pragma unmanaged   // C4949  
```
