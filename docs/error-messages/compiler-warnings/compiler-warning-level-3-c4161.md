---
title: Compilador advertencia (nivel 3) C4161 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4161
dev_langs:
- C++
helpviewer_keywords:
- C4161
ms.assetid: 03d3be61-83f1-4009-8310-8758ab67055f
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
ms.openlocfilehash: f2b28f9dc124a90c8fd279e2aafce1471c64b5a0
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-3-c4161"></a>Advertencia del compilador (nivel 3) C4161
\#pragma pragma: más elementos POP que Push  
  
 Como el código fuente contiene una extracción más que inserciones hay para la pragma ***pragma***, es posible que la pila no tenga el comportamiento esperado. Para evitar la advertencia, asegúrese de que el número de extracciones no supera el número de inserciones.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C4161:  
  
```  
// C4161.cpp  
// compile with: /W3 /LD  
#pragma pack(push, id)  
#pragma pack(pop, id)  
#pragma pack(pop, id)   // C4161, an extra pop  
  
#pragma bss_seg(".my_data1")  
int j;  
  
#pragma bss_seg(push, stack1, ".my_data2")     
int l;  
  
#pragma bss_seg(pop, stack1)  
int m;  
  
#pragma bss_seg(pop, stack1)   // C4161  
```
