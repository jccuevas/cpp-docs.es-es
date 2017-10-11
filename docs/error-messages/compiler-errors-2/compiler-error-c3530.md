---
title: Error del compilador C3530 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3530
dev_langs:
- C++
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0d66e76fc3e44a037f52aa6e217fae848f1338d2
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

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
