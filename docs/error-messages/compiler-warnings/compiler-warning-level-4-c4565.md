---
title: Compilador advertencia (nivel 4) C4565 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4565
dev_langs: C++
helpviewer_keywords: C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2cbe5e8aecd8863f0b3ba092b8d199c1032ce157
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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