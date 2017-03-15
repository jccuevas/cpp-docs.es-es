---
title: Compilador advertencia (nivel 3) C4738 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4738
dev_langs:
- C++
helpviewer_keywords:
- C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 4c05725e155f4b3f5de4a17f66ae15d3b2885a1e
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-3-c4738"></a>Advertencia del compilador (nivel 3) C4738
almacenando el resultado flotante de 32 bits en memoria; posible pérdida de rendimiento  
  
 C4738 advierte que el resultado de una asignación, conversión, pasa el argumento o que otra operación que necesite redondear o que la operación se ha quedado sin registros y necesarios para usar memoria (derrame). Esto puede provocar la pérdida de rendimiento.  
  
 Para resolver esta advertencia y evitar el redondeo, compile con [/fp: Fast](../../build/reference/fp-specify-floating-point-behavior.md) o use `double`s en lugar de `float`s.  
  
 Para resolver esta advertencia y no quedarse sin registros, cambiar el orden de cálculo y modifique el uso de inclusión  
  
 De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4738:  
  
```  
// C4738.cpp  
// compile with: /c /fp:precise /O2 /W3  
// processor: x86  
#include <stdio.h>  
  
#pragma warning(default : 4738)  
  
float func(float f)  
{  
    return f;  
}  
  
int main()  
{  
    extern float f, f1, f2;  
    double d = 0.0;  
  
    f1 = func(d);  
    f2 = (float) d;  
    f = f1 + f2;   // C4738  
    printf_s("%f\n", f);  
}  
```
