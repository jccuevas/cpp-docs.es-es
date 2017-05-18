---
title: Error del compilador C3483 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3483
dev_langs:
- C++
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: f0bef8bd1a49eb6be611421ebbbd8364032f747a
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3483"></a>Error del compilador C3483
'var' ya forma parte de la lista de capturas lambda  
  
 Pasó la misma variable a la lista de capturas de una expresión lambda más de una vez.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Quite todas las instancias adicionales de la variable de la lista de capturas.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C3483 porque la variable `n` aparece más de una vez en la lista de capturas de la expresión lambda:  
  
```  
// C3483.cpp  
  
int main()  
{  
   int m = 6, n = 5;  
   [m,n,n] { return n + m; }(); // C3483  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)
