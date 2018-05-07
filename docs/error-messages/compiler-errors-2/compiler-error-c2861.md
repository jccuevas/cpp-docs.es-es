---
title: Error del compilador C2861 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2861
dev_langs:
- C++
helpviewer_keywords:
- C2861
ms.assetid: 012bb44d-6c9b-4def-b54e-b19f1f8ddd1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e1f7010ca6d98c4c27f85ecc858cf7703a87e90
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2861"></a>Error del compilador C2861
'nombre de la función': no se puede definir una función de miembro de interfaz  
  
 El compilador encontró la palabra clave interface o dedujo struct como una interfaz, pero, a continuación, se encontró un miembro de la definición de función.  Una interfaz no puede contener una definición de una función miembro.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C2861:  
  
```  
// C2861.cpp  
// compile with: /c  
#include <objbase.h>   // required for IUnknown definition  
[ object, uuid("00000000-0000-0000-0000-000000000001") ]  
__interface IMyInterface : IUnknown {  
   HRESULT mf(int a);  
};  
  
HRESULT IMyInterface::mf(int a) {}   // C2861  
  
```