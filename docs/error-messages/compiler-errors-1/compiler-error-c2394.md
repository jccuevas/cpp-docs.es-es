---
title: Error del compilador C2394 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2394
dev_langs:
- C++
helpviewer_keywords:
- C2394
ms.assetid: 653fa9a0-29b3-48aa-bc01-82f98f717a2b
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c716a3562a9f99ef0094d8ca7ba5fdf2d11f15f0
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2394"></a>Error del compilador C2394
'your_type' ": CLR o WinRToperator no es válido. Al menos un parámetro debe ser de los tipos siguientes: 'T^', 'T^%', 'T^&', donde T = 'su_tipo'  
  
 Un operador en un tipo administrado o en Windows Runtime no tenía al menos un parámetro con un tipo igual al del valor devuelto del operador.  
  
 El código siguiente genera el error C2394:  
  
```  
// C2394.cpp  
// compile with: /clr /c  
ref struct Y {  
   static Y^ operator -(int i, char c);   // C2394  
  
   // OK  
   static Y^ operator -(Y^ hY, char c);  
   // or  
   static Y^ operator -(int i, Y^& rhY);  
};  
```
