---
title: Error del compilador C2346 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2346
dev_langs:
- C++
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: bf0133aba65b8477bd949cd90b51edbd407bcda7
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2346"></a>Error del compilador C2346
'función' no se pueden compilar como nativa: razón  
  
 El compilador no pudo compilar una función en MSIL.  
  
 Para obtener más información, consulte [managed, unmanaged](../../preprocessor/managed-unmanaged.md) y [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Quite el código en la función que no se pueden compilar en MSIL.  
  
2.  No tendrá que compilar el módulo con **/CLR**, o marque la función como no administrados con la directiva pragma no administrada.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2346.  
  
```  
// C2346.cpp  
// processor: x86  
// compile with: /clr   
// C2346 expected  
struct S  
{  
   S()  
   {  
      { __asm { nop } }  
   }  
   virtual __clrcall ~S() { }  
};  
  
void main()  
{  
   S s;  
}  
```
