---
title: Error del compilador C3609 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3609
dev_langs:
- C++
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: eb5d5127020ad1855c3fe7d94c362deeee53ccad
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3609"></a>Error del compilador C3609
'member': una función sealed o final debe ser virtual  
  
 El [sellado](../../windows/sealed-cpp-component-extensions.md) y [final](../../cpp/final-specifier.md) palabras clave solo se permite en una función de clase, struct o miembro marcada `virtual`.  
  
 El ejemplo siguiente genera el error C3609:  
  
```  
// C3609.cpp  
// compile with: /clr /c  
ref class C {  
   int f() sealed;   // C3609  
   virtual int f2() sealed;   // OK  
};  
```  

