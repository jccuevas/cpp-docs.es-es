---
title: Compilador advertencia (nivel 1) C4090 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4090
dev_langs:
- C++
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a28924b2cf176524a2ecd3156394dd7530cfb9f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4090"></a>Compilador advertencia (nivel 1) C4090
'operación': calificadores 'modificador' diferentes  
  
 Se define una variable que se usa en una operación con un modificador especificado que impide que se modifiquen sin ser detectado por el compilador. La expresión se compila sin ninguna modificación.  
  
 Esta advertencia puede producirse cuando un puntero a un **const** o `volatile` elemento se asigna a un puntero no declarado como puntero a **const** o `volatile`.  
  
 Esta advertencia se emite para programas de C. En un programa de C++, el compilador emite un error: [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).  
  
 El ejemplo siguiente genera C4090:  
  
```  
// C4090.c  
// compile with: /W1  
int *volatile *p;  
int *const *q;  
int **r;  
  
int main() {  
   p = q;   // C4090  
   p = r;  
   q = p;   // C4090  
   q = r;  
   r = p;   // C4090  
   r = q;   // C4090  
}  
```