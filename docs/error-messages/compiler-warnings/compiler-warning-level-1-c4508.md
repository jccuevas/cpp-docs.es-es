---
title: Compilador advertencia (nivel 1) C4508 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4508
dev_langs:
- C++
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53f152c2f3573e5f3bd7b8e9be0603ed6d3f11bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4508"></a>Advertencia del compilador (nivel 1) C4508
'función': función debe devolver un valor; 'void' tipo de valor devuelto supone  
  
 La función no tiene especificado ningún tipo de valor devuelto. En este caso, también se desencadena C4430 y el compilador implementa la corrección indicada por C4430 (el valor predeterminado es de tipo int).  
  
 Para resolver esta advertencia, declare explícitamente el tipo de valor devuelto de funciones.  
  
 El ejemplo siguiente genera C4508:  
  
```  
// C4508.cpp  
// compile with: /W1 /c  
#pragma warning (disable : 4430)  
func() {}   // C4508  
void func2() {}   // OK  
```