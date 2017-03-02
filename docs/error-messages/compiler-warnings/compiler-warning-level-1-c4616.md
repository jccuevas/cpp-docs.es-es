---
title: Compilador advertencia (nivel 1) C4616 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4616
dev_langs:
- C++
helpviewer_keywords:
- C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 584a07701717afc40a738cf4088ec9cab2d98c0a
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4616"></a>Advertencia del compilador (nivel 1) C4616
\#advertencia pragma: número de advertencia 'número' no es una advertencia válida del compilador  
  
 El número de advertencia especificado en el [advertencia](../../preprocessor/warning.md) pragma no se puede reasignar. Se ha omitido la pragma.  
  
 El ejemplo siguiente genera C4616:  
  
```  
// C4616.cpp  
// compile with: /W1 /c  
#pragma warning( disable : 0 )   // C4616  
#pragma warning( disable : 999 )   // OK  
#pragma warning( disable : 4998 )   // OK  
```
