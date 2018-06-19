---
title: Error del compilador C3493 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3493
dev_langs:
- C++
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3aec62bfff59396ec73141746193e4e3f16d84fa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257321"
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