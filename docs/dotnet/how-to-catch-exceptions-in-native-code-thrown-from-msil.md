---
title: "C&#243;mo: Detectar excepciones en c&#243;digo nativo iniciadas desde MSIL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "detectar excepciones, producidas a partir de MSIL"
  - "excepciones, detectar"
  - "MSIL, detectar excepciones en código nativo"
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# C&#243;mo: Detectar excepciones en c&#243;digo nativo iniciadas desde MSIL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En código nativo, puede detectar excepciones de C\+\+ nativo de MSIL.  Puede detectar las excepciones de CLR con `__try` y `__except`.  
  
 Para obtener más información, vea [Control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md) y [Control de excepciones de C\+\+](../cpp/cpp-exception-handling.md).  
  
## Ejemplo  
 El ejemplo siguiente se define un módulo con dos funciones, una que produce una excepción nativa, y otra que produce una excepción de MSIL.  
  
```  
// catch_MSIL_in_native.cpp  
// compile with: /clr /c  
void Test() {  
   throw ("error");  
}  
  
void Test2() {  
   throw (gcnew System::Exception("error2"));  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente define un módulo que detecte un natural y una excepción de MSIL.  
  
```  
// catch_MSIL_in_native_2.cpp  
// compile with: /clr catch_MSIL_in_native.obj  
#include <iostream>  
using namespace std;  
void Test();  
void Test2();  
  
void Func() {  
   // catch any exception from MSIL  
   // should not catch Visual C++ exceptions like this  
   // runtime may not destroy the object thrown  
   __try {  
      Test2();  
   }  
   __except(1) {  
      cout << "caught an exception" << endl;  
   }  
  
}  
  
int main() {  
   // catch native C++ exception from MSIL  
   try {  
      Test();  
   }  
   catch(char * S) {  
      cout << S << endl;  
   }  
   Func();  
}  
```  
  
  **error**  
**cogió una excepción**   
## Vea también  
 [Control de excepciones](../windows/exception-handling-cpp-component-extensions.md)