---
title: Error del compilador C2500 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2500
dev_langs:
- C++
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 2b869ca0ba959e9b774a005298ef4456d0995156
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2500"></a>Error del compilador C2500
'identificador1': 'identificador2' ya es una clase base directa  
  
 Una clase o estructura aparece más de una vez en una lista de clases base.  
  
 Una base directa es una mencionada en la lista base. Una base indirecta es una clase base de una de las clases en la lista base.  
  
 Una clase no puede especificarse como una clase base directa más de una vez. Una clase puede utilizarse como una clase base indirecta más de una vez.  
  
 El ejemplo siguiente genera C2500:  
  
```  
// C2500.cpp  
// compile with: /c  
class A {};  
class B : public A, public A {};    // C2500  
  
// OK  
class C : public A {};  
class D : public A {};  
class E : public C, public D {};  
```
