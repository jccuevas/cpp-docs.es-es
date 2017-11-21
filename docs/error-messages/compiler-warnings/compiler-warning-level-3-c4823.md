---
title: Compilador advertencia (nivel 3) C4823 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4823
dev_langs: C++
helpviewer_keywords: C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: af4b7e220957722793458a283244092574d05fa9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4823"></a>Advertencia del compilador (nivel 3) C4823
'función': utiliza punteros anclados de desenredo pero una semántica no está habilitada. Considere el uso de /EHa  
  
Para desanclar un objeto del montón administrado que señala un puntero anclado declarado en un ámbito de bloque, el compilador simula el comportamiento de los destructores de las clases locales, "fingiendo" que el puntero anclado tenga un destructor que anula el puntero. Para habilitar una llamada a un destructor después de producir una excepción, debe habilitar desenredo de objetos, lo que puede hacer mediante el uso de [/EHsc](../../build/reference/eh-exception-handling-model.md).  
  
También manualmente puede Desanclar el objeto y pasar por alto la advertencia.  
  
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
