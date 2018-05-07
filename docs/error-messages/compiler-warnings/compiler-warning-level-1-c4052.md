---
title: Compilador advertencia (nivel 1) C4052 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4052
dev_langs:
- C++
helpviewer_keywords:
- C4052
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5c937e602f14789419f6b124034503c127f6dc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4052"></a>Advertencia del compilador (nivel 1) C4052
las declaraciones de función son distintas; una de ellas contiene argumentos de variable  
  
 Una declaración de la función no contiene argumentos de variable. Se omite.  
  
 El ejemplo siguiente genera la advertencia C4052:  
  
```  
// C4052.c  
// compile with: /W4 /c  
int f();  
int f(int i, ...);   // C4052  
```