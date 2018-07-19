---
title: Compilador advertencia (nivel 1) C4616 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4616
dev_langs:
- C++
helpviewer_keywords:
- C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6cf59fa32b45215cc29c1cc500cc0bef3378b51e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282709"
---
# <a name="compiler-warning-level-1-c4616"></a>Advertencia del compilador (nivel 1) C4616
\#Advertencia de pragma: número de advertencia 'número' no es una advertencia válida del compilador  
  
 El número de advertencia especificado en el [advertencia](../../preprocessor/warning.md) pragma no se pueden reasignar. Se omitió la directiva pragma.  
  
 El ejemplo siguiente genera C4616:  
  
```  
// C4616.cpp  
// compile with: /W1 /c  
#pragma warning( disable : 0 )   // C4616  
#pragma warning( disable : 999 )   // OK  
#pragma warning( disable : 4998 )   // OK  
```