---
title: Error del compilador C2395 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2395
dev_langs:
- C++
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 411a8d62de801591ff6a90a7bf74f3b2cfe67c7a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225435"
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