---
title: Error del compilador C3824 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3824
dev_langs:
- C++
helpviewer_keywords:
- C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 529e881d8872d3ea1d69da14ac393282c4f3efc1
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3824"></a>Error del compilador C3824
'member': este tipo no puede aparecer en este contexto (parámetro de función, tipo de valor devuelto o un miembro estático)  
  
 Punteros anclados no pueden ser parámetros de función, tipos de valor devuelto o declarados `static`.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3824:  
  
```  
// C3824a.cpp  
// compile with: /clr /c  
void func() {  
   static pin_ptr<int> a; // C3824  
   pin_ptr<int> b; // OK  
}  
```  

