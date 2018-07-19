---
title: Error del compilador C3536 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3536
dev_langs:
- C++
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f88e656b0d63b6a7a4d60ace2f4cd5e2347d188
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250292"
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