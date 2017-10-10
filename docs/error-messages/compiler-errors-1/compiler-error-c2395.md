---
title: Error del compilador C2395 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2395
dev_langs:
- C++
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 9190f4ef8a9db2daa29c6e2c3a59e0152c05d38a
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2395"></a>Error del compilador C2395
'your_type::operator'op'': el operador CLR o WinRT no es válido. Al menos un parámetro debe ser de los tipos siguientes: 'T', 'T%', 'T&', 'T^', 'T^%', 'T^&', donde T = 'su_tipo'  
  
 Un operador en un tipo administrado o en Windows Runtime no tenía al menos un parámetro con un tipo igual al del valor devuelto del operador.  
  
 El ejemplo siguiente genera C2395 y muestra cómo corregirlo:  
  
```  
// C2395.cpp  
// compile with: /clr /c  
value struct V {  
   static V operator *(int i, char c);   // C2395  
  
   // OK  
   static V operator *(V v, char c);  
   // or  
   static V operator *(int i, V& rv);  
};  
```
