---
title: Error del compilador C2427 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2427
dev_langs:
- C++
helpviewer_keywords:
- C2427
ms.assetid: a7d421af-6180-40b4-b7a6-9f3bc7dfaaf9
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 416db305963b6357c6dce9c5b2d13f0a6ca186f3
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2427"></a>Error del compilador C2427
'clase': no se puede definir la clase en este ámbito  
  
 Se ha intentado definir una clase anidada, pero la clase anidada es un miembro de una clase base, no la clase contenedora más.  
  
 El ejemplo siguiente genera C2427:  
  
```  
// C2427.cpp  
// compile with: /c  
template <class T>   
struct S {  
   struct Inner;   
};   
  
struct Y : S<int> {};   
  
struct Y::Inner {};   // C2427  
  
// OK  
template<typename T>  
struct S<T>::Inner {};  
```
