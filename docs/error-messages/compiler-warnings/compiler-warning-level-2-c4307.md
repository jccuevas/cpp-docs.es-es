---
title: Compilador advertencia (nivel 2) C4307 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4307
dev_langs:
- C++
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52914fc5825bda5647308c006b853538f3d6225e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292037"
---
# <a name="compiler-warning-level-2-c4307"></a>Advertencia del compilador (nivel 2) C4307
'operador': desbordamiento de constante integral  
  
 Este operador se usa en una expresión que da como resultado una constante entera que desborda el espacio asignado para él. Debe usar un tipo mayor para la constante. A **firmado int** contiene un valor más pequeño que un `unsigned int` porque el **firmado int** utiliza un bit para representar el inicio de sesión.  
  
 El ejemplo siguiente genera C4307:  
  
```  
// C4307.cpp  
// compile with: /W2  
int i = 2000000000 + 2000000000;   // C4307  
int j = (unsigned)2000000000 + 2000000000;   // OK  
  
int main()  
{  
}  
```