---
title: Error del compilador C3363 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3363
dev_langs:
- C++
helpviewer_keywords:
- C3363
ms.assetid: 41aa922f-608e-4f7a-ba66-451fc1161935
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: dc791e83ced4a7dc0aa8f7f64c685b4a0d68a0ed
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3363"></a>Error del compilador C3363
'tipo': 'typeid' solamente se puede asignar a un tipo.  
  
 El [typeid](../../windows/typeid-cpp-component-extensions.md) operador se usó incorrectamente.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3363.  
  
```  
// C3363.cpp  
// compile with: /clr  
int main() {  
   System::typeid;   // C3363  
}  
```
