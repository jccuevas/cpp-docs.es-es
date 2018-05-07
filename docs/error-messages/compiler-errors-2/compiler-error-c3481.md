---
title: Error del compilador C3481 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3481
dev_langs:
- C++
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77fc0f542a74cb077e59882e31dd1acb10c7b7e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3481"></a>Error del compilador C3481
'var': no se encuentra la variable de captura lambda  
  
 El compilador no puede encontrar la definición de una variable que se pasó a la lista de capturas de una expresión lambda.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Quite la variable de la lista de capturas de la expresión lambda.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C3481 porque la variable `n` no está definida:  
  
```  
// C3481.cpp  
  
int main()  
{  
   [n] {}(); // C3481  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)