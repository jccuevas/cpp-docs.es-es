---
title: Error irrecuperable C1016 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1016
dev_langs:
- C++
helpviewer_keywords:
- C1016
ms.assetid: 33f45c3e-2d8f-43ad-a445-c412d1d54ce1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8a07f1fc36293b483772087b3325c7e0d0529e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1016"></a>Error irrecuperable C1016
\#ifdef esperaba que un identificador, #ifndef esperaba un identificador  
  
 La directiva de compilación condicional ([#ifdef](../../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md) o `#ifndef`) no tiene ningún identificador que evaluar. Para resolver el error, especifique un identificador.  
  
 El ejemplo siguiente genera la advertencia C1016:  
  
```  
// C1016.cpp  
#ifdef   // C1016  
#define FC1016  
#endif  
  
int main() {}  
```  
  
 Posible resolución:  
  
```  
// C1016b.cpp  
#ifdef X  
#define FC1016  
#endif  
  
int main() {}  
```