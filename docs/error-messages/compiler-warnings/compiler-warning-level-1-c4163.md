---
title: Compilador advertencia (nivel 1) C4163 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4163
dev_langs:
- C++
helpviewer_keywords:
- C4163
ms.assetid: b08413fd-03fc-4f41-9167-a98976ac12f2
caps.latest.revision: 7
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
ms.openlocfilehash: 2bfe06b1eb7c05389194d628330515b64e3f8eb7
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4163"></a>Advertencia del compilador (nivel 1) C4163
'identifier': no está disponible como función intrínseca.  
  
 No se puede usar la función especificada como un [intrínseco](../../preprocessor/intrinsic.md) (función). El compilador omite el nombre de función no válido.  
  
 El ejemplo siguiente genera la advertencia C4163:  
  
```  
// C4163.cpp  
// compile with: /W1 /LD  
#include <math.h>  
#pragma intrinsic(mysin)   // C4163  
// try the following line instead  
// #pragma intrinsic(sin)  
```
