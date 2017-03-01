---
title: Compilador advertencia (nivel 1) C4006 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4006
dev_langs:
- C++
helpviewer_keywords:
- C4006
ms.assetid: f1a59819-0fd2-4361-8e3a-99e4b514b8e1
caps.latest.revision: 6
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: dd2b1f3501a3dd806e160d23b7160191428b26b1
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4006"></a>Advertencia del compilador (nivel 1) C4006
\#undef esperaba un identificador  
  
 La directiva `#undef` no especificó un identificador al que quitar la definición. Se omitió la directiva. Para resolver la advertencia, asegúrese de especificar un identificador. El ejemplo siguiente genera la advertencia C4006:  
  
```  
// C4006.cpp  
// compile with: /W1  
#undef   // C4006  
  
// try..  
// #undef TEST  
  
int main() {  
}  
```
