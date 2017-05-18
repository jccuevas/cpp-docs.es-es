---
title: Error del compilador C2293 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2293
dev_langs:
- C++
helpviewer_keywords:
- C2293
ms.assetid: 17e7b4e2-368b-4dd7-a01b-d82be60f8e56
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 517f2f31c012f3d8c45fdd93fb2132b12bddd229
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2293"></a>Error del compilador C2293
'identifier': no se puede tener una variable miembro como especificador __based  
  
 Los especificadores del modificador `__based` deben ser punteros no miembros.  
  
 El ejemplo siguiente genera la advertencia C2293:  
  
```  
// C2293.cpp  
// compile with: /c  
class A {  
   static int *i;  
   void __based(i) *bp;   // C2293  
   void *bp2;   // OK  
};  
```
