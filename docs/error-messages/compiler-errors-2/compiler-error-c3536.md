---
title: Error del compilador C3536 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3536
dev_langs:
- C++
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 90db065c9a16e72a396bd1c1ae54bb99cdb97153
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3536"></a>Error del compilador C3536
'símbolo': no se puede usar antes de inicializarse  
  
 No se puede usar el símbolo indicado antes de inicializarlo. En la práctica, esto significa que una variable no se puede usar para inicializarse a sí misma.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  No se inicialice una variable a sí mismo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera el error C3536 porque cada variable se inicializa con el propio.  
  
```  
// C3536.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto a = a;     //C3536  
   auto b = &b;    //C3536  
   auto c = c + 1; //C3536  
   auto* d = &d;   //C3536  
   auto& e = e;    //C3536  
   return 0;  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Auto (palabra clave)](../../cpp/auto-keyword.md)
