---
title: Error del compilador C3493 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3493
dev_langs:
- C++
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
caps.latest.revision: 6
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
ms.openlocfilehash: 99fc958e4873d13bbc413f556e505ec7224443a5
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3493"></a>Error del compilador C3493
'var' no se puede capturar de forma implícita porque no se ha especificado ningún modo de captura predeterminado  
  
 La captura de la expresión lambda vacía, `[]`, especifica que la expresión lambda no captura de forma explícita ni implícita ninguna variable.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Proporcione un modo de captura predeterminado, o bien  
  
-   Capture explícitamente una o varias variables.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C3493 porque modifica una variable externa, pero especifica la cláusula de captura vacía:  
  
```  
// C3493a.cpp  
  
int main()  
{  
   int m = 55;  
   [](int n) { m = n; }(99); // C3493  
}  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente resuelve el error C3493 especificando mediante referencia como el modo de captura predeterminado.  
  
```  
// C3493b.cpp  
  
int main()  
{  
   int m = 55;  
   [&](int n) { m = n; }(99);  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)
