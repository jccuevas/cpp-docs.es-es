---
title: Compilador advertencia (nivel 1) C4081 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4081
dev_langs:
- C++
helpviewer_keywords:
- C4081
ms.assetid: 6f656373-a080-4989-bbc9-e2f894b03293
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a55ee972e16655ab93ab463417718eb879ef2477
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4081"></a>Advertencia del compilador (nivel 1) C4081
se esperaba 'token1'; se encontró 'token2'  
  
 El compilador esperaba un token distinto en este contexto.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4081.cpp  
// compile with: /W1 /LD  
#pragma optimize) "l", on )   // C4081  
```