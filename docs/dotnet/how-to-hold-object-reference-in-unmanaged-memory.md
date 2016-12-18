---
title: "C&#243;mo: Mantener una referencia a objeto en la memoria no administrada | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "gcroot (palabra clave) [C++], referencia a objeto en una función nativa"
  - "referencias a objetos, en funciones nativas"
  - "objetos [C++], referencia en funciones nativas"
  - "referencias, a objetos en funciones nativas"
ms.assetid: a61eb8ce-3982-477d-8d3d-2173fd57166d
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Mantener una referencia a objeto en la memoria no administrada
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede utilizar gcroot.h, que encapsula a <xref:System.Runtime.InteropServices.GCHandle>, para guardar la referencia a un objeto de CLR en memoria no administrada.  Como alternativa, puede utilizar `GCHandle` directamente.  
  
## Ejemplo  
  
```  
// hold_object_reference.cpp  
// compile with: /clr  
#include "gcroot.h"  
using namespace System;  
  
#pragma managed  
class StringWrapper {  
  
private:  
   gcroot<String ^ > x;  
  
public:  
   StringWrapper() {  
      String ^ str = gcnew String("ManagedString");  
      x = str;  
   }  
  
   void PrintString() {  
      String ^ targetStr = x;  
      Console::WriteLine("StringWrapper::x == {0}", targetStr);  
   }  
};  
#pragma unmanaged  
int main() {  
   StringWrapper s;  
   s.PrintString();  
}  
```  
  
  **StringWrapper::x \=\= ManagedString**   
## Ejemplo  
 `GCHandle` proporciona un medio para guardar la referencia a un objeto administrado en memoria no administrada.  Puede utilizar el método <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> para crear un identificador opaco a un objeto administrado y <xref:System.Runtime.InteropServices.GCHandle.Free%2A> para liberarlo.  Además, el método <xref:System.Runtime.InteropServices.GCHandle.Target%2A> permite obtener de nuevo la referencia al objeto a partir del identificador en código administrado.  
  
```  
// hold_object_reference_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma managed  
class StringWrapper {  
   IntPtr m_handle;  
public:  
   StringWrapper() {  
      String ^ str = gcnew String("ManagedString");  
      m_handle = static_cast<IntPtr>(GCHandle::Alloc(str));  
   }  
   ~StringWrapper() {  
      static_cast<GCHandle>(m_handle).Free();  
   }  
  
   void PrintString() {  
      String ^ targetStr = safe_cast< String ^ >(static_cast<GCHandle>(m_handle).Target);  
      Console::WriteLine("StringWrapper::m_handle == {0}", targetStr);  
   }  
};  
  
#pragma unmanaged  
int main() {  
   StringWrapper s;   
   s.PrintString();  
}  
```  
  
  **StringWrapper::m\_handle \=\= ManagedString**   
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)