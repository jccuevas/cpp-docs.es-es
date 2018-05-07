---
title: Compilador advertencia (nivel 3) C4823 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4823
dev_langs:
- C++
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c29499a82601dcf653ff2f003441935f1d6841a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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
