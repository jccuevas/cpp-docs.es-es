---
title: Error del compilador C2233 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2233
dev_langs:
- C++
helpviewer_keywords:
- C2233
ms.assetid: 236bdf0b-9607-4f26-a249-d8def0b1333c
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 532199b3df2aaa1c81b23797bfb379c3ed828cd4
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2233"></a>Error del compilador C2233
'identificador': las matrices de objetos que contienen matrices de tamaño cero no son válidas  
  
 Cada objeto de matriz debe contener al menos un elemento.  
  
 El ejemplo siguiente genera C2233:  
  
```  
// C2233.cpp  
// compile with: /c  
class A {  
   char somearray[1];  
};  
  
class B {  
   char zeroarray[];  
};  
  
A array[100];   // OK  
B array2[100];   // C2233  
```
