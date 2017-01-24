---
title: "Error del compilador C3642 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3642"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3642"
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3642
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'return\_type\/args' : no se puede llamar a una función con la convención de llamada \_\_clrcall desde código nativo  
  
 No se puede llamar a una función marcada con la convención de llamada [\_\_clrcall](../../cpp/clrcall.md) desde código nativo \(no administrado\).  
  
 *return\_type\/args* es el nombre de la función o el tipo de función de `__clrcall` que está intentando llamar.  Se utiliza un tipo cuando la llamada se realiza a través de un puntero a una función.  
  
 Para llamar a una función administrada desde un contexto nativo, puede agregar una función "contenedor" que llamará a la función `__clrcall`.  También puede usar el mecanismo de cálculo de referencias de CLR; para obtener más información, vea [Cómo: Calcular las referencias de punteros a función mediante PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md).  
  
 El código siguiente genera el error C3642:  
  
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