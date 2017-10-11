---
title: Error del compilador C2396 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2396
dev_langs:
- C++
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 20eca11d402265bbc81d61a8079ae9975cceef67
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2396"></a>Error del compilador C2396
' your_type '': CLR o WinRT functionnot de conversión definida por el usuario válida. Debe convertir de o a: 'T^', 'T^%', 'T^&', donde T = 'your_type'  
  
 Una función de conversión en un tipo administrado o de Windows Runtime no tenía al menos un parámetro con un tipo igual al tipo que contiene la función de conversión.  
  
 El siguiente ejemplo genera el error C2396 y muestra cómo corregirlo:  
  
```  
// C2396.cpp  
// compile with: /clr /c  
  
ref struct Y {  
   static operator int(char c);   // C2396  
  
   // OK  
   static operator int(Y^ hY);  
   // or  
   static operator Y^(char c);  
};  
```
