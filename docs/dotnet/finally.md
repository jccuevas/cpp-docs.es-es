---
title: "finally | Microsoft Docs"
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
  - "finally (palabra clave) [C++]"
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# finally
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Además de `try` y las cláusulas de `catch` , el control de excepciones de CLR admite una cláusula de `finally` .  La semántica es idéntica a `__finally` bloqueado en el control estructurado de excepciones \(SEH\).  Un bloque de `__finally` puede seguir un bloque de `try` o de `catch` .  
  
## Comentarios  
 El propósito del bloque de `finally` es limpiar los recursos está después de la excepción producida.  Observe que el bloque de `finally` se ejecutará siempre, aunque no se produjo ninguna excepción.  El bloque de `catch` sólo se ejecuta si una excepción administrada se produce dentro del bloque asociado de `try` .  
  
 `finally` es una palabra clave contextual; vea [Palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md) para obtener más información.  
  
## Ejemplo  
 El ejemplo siguiente se muestra `finally` simple bloqueos:  
  
```  
// keyword__finally.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyException: public System::Exception{};  
  
void ThrowMyException() {  
   throw gcnew MyException;  
}  
  
int main() {  
   try {  
      ThrowMyException();  
   }  
   catch ( MyException^ e ) {  
      Console::WriteLine(  "in catch" );  
      Console::WriteLine( e->GetType() );  
   }  
   finally {  
      Console::WriteLine(  "in finally" );  
   }  
}  
```  
  
  **en captura**  
**MyException**  
**en finalmente**   
## Vea también  
 [Control de excepciones](../windows/exception-handling-cpp-component-extensions.md)