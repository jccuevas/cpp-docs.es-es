---
title: Error del compilador C2346 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2346
dev_langs:
- C++
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9459d7330738180e92776e93fcba9a07bfd39640
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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