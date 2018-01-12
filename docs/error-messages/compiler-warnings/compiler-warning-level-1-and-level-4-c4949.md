---
title: Compilador (niveles 1 y 4) C4949 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4949
dev_langs: C++
helpviewer_keywords: C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3d23a6d6e030007289cc50ce0372acc8f99e7ed3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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