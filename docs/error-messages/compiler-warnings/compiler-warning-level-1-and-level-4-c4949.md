---
title: Compilador (niveles 1 y 4) C4949 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4949
dev_langs:
- C++
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3dbf80f85db7334d4bcb46402851cac601d258f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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