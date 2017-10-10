---
title: Error del compilador C2160 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2160
dev_langs:
- C++
helpviewer_keywords:
- C2160
ms.assetid: a1f694a7-fb16-4437-b7f5-a1af6da94bc5
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: caef1127e06bbf0b12480b2c10239c77ae6c0ad5
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2160"></a>Error del compilador C2160
'##' no puede aparecer al principio de una definición de macro  
  
 Una definición de macro comenzaba con un operador de pegado de token (##).  
  
 El ejemplo siguiente genera la advertencia C2160:  
  
```  
// C2160.cpp  
// compile with: /c  
#define mac(a,b) #a   // OK  
#define mac(a,b) ##a   // C2160  
```
