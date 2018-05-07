---
title: Compilador advertencia (nivel 1) C4806 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4806
dev_langs:
- C++
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92d5b36a653680285523c7cebb605238b37d57c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4806"></a>Advertencia del compilador (nivel 1) C4806
'operación': operación no segura: ningún valor del tipo 'tipo' promovido al tipo 'tipo' puede igualar la constante proporcionada.  
  
 Este mensaje advierte de código como `b == 3`, donde `b` tiene un tipo `bool`. Las reglas de promoción provocan que `bool` se promueva a `int`. Está permitido, pero nunca puede ser **true**. El ejemplo siguiente genera la advertencia C4806:  
  
```  
// C4806.cpp  
// compile with: /W1  
int main()  
{  
   bool b = true;  
   // try..  
   // int b = true;  
  
   if (b == 3)   // C4806  
   {  
      b = false;  
   }  
}  
```