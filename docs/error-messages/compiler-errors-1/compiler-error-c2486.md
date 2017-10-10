---
title: Error del compilador C2486 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2486
dev_langs:
- C++
helpviewer_keywords:
- C2486
ms.assetid: 436da349-6461-4e32-bfca-4f3e620108e2
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: b7f54417beefb9bd2c82763464d0e76ed81bf7ed
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2486"></a>Error del compilador C2486
'__LOCAL_SIZE' sólo se permite en la función con el atributo 'naked'  
  
 En las funciones de ensamblado en línea, el nombre `__LOCAL_SIZE` está reservado para las funciones declaradas con el [naked](../../cpp/naked-cpp.md) atributo.  
  
 El ejemplo siguiente genera C2486:  
  
```  
// C2486.cpp  
// processor: x86  
void __declspec(naked) f1() {  
   __asm {  
      mov   eax,   __LOCAL_SIZE  
   }  
}  
void f2() {  
   __asm {  
      mov   eax,   __LOCAL_SIZE   // C2486  
   }  
}  
```
