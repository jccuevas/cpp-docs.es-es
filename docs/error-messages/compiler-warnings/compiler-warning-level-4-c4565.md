---
title: Compilador advertencia (nivel 4) C4565 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4565
dev_langs:
- C++
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3c4249783686c1fabb44395d3c092eca0d9230a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293369"
---
# <a name="compiler-warning-level-4-c4565"></a>Advertencia del compilador (nivel 4) C4565
'función': nueva definición; el símbolo se declaró previamente con __declspec (modificador)  
  
 Se vuelve a definir o se volvió a declarar un símbolo de y la segunda definición o declaración, a diferencia de la primera definición o declaración, no tenía un `__declspec` modificador (***modificador***). La advertencia es informativa. Para corregir esta advertencia, elimine una de las definiciones.  
  
 El ejemplo siguiente genera C4565:  
  
```  
// C4565.cpp  
// compile with: /W4 /LD  
__declspec(noalias) void f();  
void f();   // C4565  
```