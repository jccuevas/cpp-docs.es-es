---
title: Compilador advertencia (nivel 1) C4731 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4731
dev_langs:
- C++
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31bdf972ef3791760469251dc4d0bf19627bded2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4731"></a>Advertencia del compilador (nivel 1) C4731
'pointer': 'registro' modificado por código ensamblador en línea de registro de puntero de marco  
  
 Se ha modificado un registro de puntero de marco. Debe guardar y restaurar el registro en su alineado ensamblado bloque o variable de marco (local o parámetro, según el registro modificado), o el código no funcionen correctamente.  
  
 El ejemplo siguiente genera C4731:  
  
```  
// C4731.cpp  
// compile with: /W1 /LD  
// processor: x86  
// C4731 expected  
void bad(int p) {  
   __asm  
   {  
      mov ebp, 1  
   }  
  
   if (p == 1)  
   {  
      // ...  
   }  
}  
```  
  
 EBP es el puntero de marco (no se permite FPO) y se está modificando. Cuando `p` es posterior al que hace referencia, se hace referencia relativa a `EBP`. Pero `EBP` se ha sobrescrito por el código, por lo que el programa no funcionará correctamente e incluso puede producir un error.