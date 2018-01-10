---
title: "Por último | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dd357c8eeed9eddc6940ce02de6e5d2b4f8c68d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="finally"></a>finally
Además `try` y `catch` admite el control de excepciones de CLR, en un `finally` cláusula. La semántica es idéntica a la `__finally` bloque de excepciones estructurado (SEH). A `__finally` bloque puede seguir un `try` o `catch` bloque.  
  
## <a name="remarks"></a>Comentarios  
 El propósito de la `finally` bloque es limpiar los recursos que queden después de que se produjo la excepción. Tenga en cuenta que el `finally` bloque se ejecuta siempre, incluso si se ha producido ninguna excepción. El `catch` bloque solo se ejecuta si se produce una excepción administrada en el asociado `try` bloque.  
  
 `finally`es una palabra clave contextual; vea [palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un sencillo `finally` bloque:  
  
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
  
```Output  
in catch  
MyException  
in finally  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../windows/exception-handling-cpp-component-extensions.md)