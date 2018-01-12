---
title: Error del compilador C3642 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3642
dev_langs: C++
helpviewer_keywords: C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3dace0204f4534ee630924bd443d028efc2afc14
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3642"></a>Error del compilador C3642
' return_type/args': no se puede llamar a una función con la convención de llamada de código nativo __clrcall  
  
 Una función que se marca con la [__clrcall](../../cpp/clrcall.md) convención de llamada no se puede llamar desde código nativo (no administrado).  
  
 *return_type/args* es el nombre de la función o el tipo de la `__clrcall` función que está intentando llamar.  Se utiliza un tipo al que está llamando a través de un puntero de función.  
  
 Para llamar a una función administrada desde un contexto nativo, puede agregar una función de "contenedor" que llamará el `__clrcall` función. O bien, puede usar el mecanismo de cálculo de referencias de CLR; vea [Cómo: serializar punteros de función Using PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) para obtener más información.  
  
 El ejemplo siguiente genera C3642:  
  
```  
// C3642.cpp  
// compile with: /clr  
using namespace System;  
struct S {  
   void Test(String ^ s) {   // CLR type in signature, implicitly __clrcall  
      Console::WriteLine(s);  
   }  
   void Test2(char * s) {  
      Test(gcnew String(s));  
   }  
};  
  
#pragma unmanaged  
int main() {  
   S s;  
   s.Test("abc");   // C3642  
   s.Test2("abc");   // OK  
}  
```