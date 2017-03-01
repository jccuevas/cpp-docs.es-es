---
title: C4439 de advertencia del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4439
dev_langs:
- C++
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
caps.latest.revision: 6
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
ms.openlocfilehash: b827d0d2feac4cafe4a90d58003a348ece36bd2d
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-c4439"></a>Advertencia del compilador C4439
'función': definición de función con un tipo administrado en la firma debe tener una convención de llamada __clrcall  
  
 El compilador reemplazó implícitamente una convención de llamada con [__clrcall](../../cpp/clrcall.md). Para resolver esta advertencia, quite el `__cdecl` o `__stdcall` convención de llamada.  
  
 C4439 siempre se emite como error. Puede desactivar esta advertencia con el `#pragma warning` o **/wd**; vea [advertencia](../../preprocessor/warning.md) o [/w, / W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, /Wall, /wd, y nosotros, /wo, / wv, /WX (nivel de advertencia)](../../build/reference/compiler-option-warning-level.md) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4439.  
  
```  
// C4439.cpp  
// compile with: /clr  
void __stdcall f( System::String^ arg ) {}   // C4439  
void __clrcall f2( System::String^ arg ) {}   // OK  
void f3( System::String^ arg ) {}   // OK  
```
