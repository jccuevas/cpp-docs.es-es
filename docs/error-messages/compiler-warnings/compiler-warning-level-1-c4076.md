---
title: Compilador advertencia (nivel 1) C4076 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4076
dev_langs:
- C++
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
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
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 2ab3c4160dfe920073c54854311bd58a5db422bb
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4076"></a>Advertencia del compilador (nivel 1) C4076
'typemod': no se puede utilizar con el tipo 'typename'  
  
 Un modificador de tipo, tanto si es **signed** como `unsigned`, no se puede usar con un tipo no entero. ***typemod*** se omite.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4076:  
  
```  
// C4076.cpp  
// compile with: /W1 /LD  
unsigned double x;   // C4076  
```
