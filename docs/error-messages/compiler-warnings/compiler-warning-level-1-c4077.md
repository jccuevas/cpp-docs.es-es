---
title: Compilador advertencia (nivel 1) C4077 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4077
dev_langs:
- C++
helpviewer_keywords:
- C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a558ff0ae3c33f25c4f07dc642607fd8a840c70c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275335"
---
# <a name="compiler-warning-level-1-c4077"></a>Advertencia del compilador (nivel 1) C4077
opción check_stack desconocida  
  
 El formato antiguo de la pragma **check_stack** se usa con un argumento desconocido. El argumento debe ser `+`, `-`, `(on)`, `(off)`o estar vacío.  
  
 El compilador omite la pragma y deja la comprobación de la pila sin cambios.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4077.cpp  
// compile with: /W1 /LD  
#pragma check_stack yes // C4077  
#pragma check_stack +    // Correct old form  
#pragma check_stack (on) // Correct new form  
```