---
title: Compilador advertencia (nivel 3) C4823 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4823
dev_langs:
- C++
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
caps.latest.revision: 12
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
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: ea03723f9ccae2348a47ae4894097f5cd9f8b5a1
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-3-c4823"></a>Advertencia del compilador (nivel 3) C4823
'función': utiliza punteros anclados pero desenredo semántica no está habilitada. Considere el uso de /EHa  
  
Para desanclar un objeto del montón administrado apuntado por un puntero anclado declarado en un ámbito de bloque, el compilador simulará el comportamiento de los destructores de las clases locales, "fingiendo" que el puntero anclado tenga un destructor que convierta el puntero en nulo. Para habilitar una llamada a un destructor después de iniciar una excepción, debe habilitar desenredo de objetos, lo que puede hacer mediante el uso de [/EHsc](../../build/reference/eh-exception-handling-model.md).  
  
Puede Desanclar el objeto manualmente y omitir la advertencia.  
  
## <a name="example"></a>Ejemplo  
El ejemplo siguiente genera C4823.  
  
```  
// C4823.cpp  
// compile with: /clr /W3 /EHa-  
using namespace System;  
  
ref struct G {  
   int m;  
};  
  
void f(G ^ pG) {  
   try {  
      pin_ptr<int> p = &pG->m;  
      // manually unpin, ignore warning  
      // p = nullptr;  
      throw gcnew Exception;  
   }  
   catch(Exception ^) {}  
}   // C4823 warning  
  
int main() {  
   f( gcnew G );  
}  
```  

