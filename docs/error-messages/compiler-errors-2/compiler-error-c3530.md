---
title: Error del compilador C3530 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3530
dev_langs:
- C++
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6514d655ab813ae21ecb440415f87bce63f3591
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253523"
---
# <a name="compiler-error-c3530"></a>Error del compilador C3530
'auto' no se puede combinar con ningún otro especificador de tipo  
  
 Un especificador de tipo se usa con el `auto` palabra clave.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  No use un especificador de tipo en una declaración de variable que usa el `auto` palabra clave.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera el error C3530 porque variable `x` se declara con ambos el `auto` palabra clave y tipo `int`, y dado que el ejemplo se compila con **/Zc: Auto**.  
  
```  
// C3530.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto int x;   // C3530  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Auto (palabra clave)](../../cpp/auto-keyword.md)