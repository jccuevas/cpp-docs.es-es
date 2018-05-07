---
title: Compilador advertencia (nivel 3) C4738 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4738
dev_langs:
- C++
helpviewer_keywords:
- C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50b94cde2f8809b8ce56dc599804d11b8d058166
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4738"></a>Advertencia del compilador (nivel 3) C4738
almacenando el resultado flotante de 32 bits en memoria; posible pérdida de rendimiento  
  
 C4738 advierte que el resultado de una asignación, conversión, pasa el argumento o que otra operación que necesite redondearse o que la operación se ha quedado sin registros y necesarios para usar la memoria (verter). Esto puede dar lugar a pérdida de rendimiento.  
  
 Para resolver esta advertencia y evitar el redondeo, compile con [/fp: Fast](../../build/reference/fp-specify-floating-point-behavior.md) o use `double` en lugar de `float`.  
  
 Para resolver esta advertencia y no quedarse sin registros, cambiar el orden de cálculo y modifique el uso de inserción  
  
 De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
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