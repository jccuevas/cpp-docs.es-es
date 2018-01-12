---
title: Compilador advertencia (nivel 1) C4731 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4731
dev_langs: C++
helpviewer_keywords: C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9d8c59a22166c3f4f44db3bea43e241a2199009d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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