---
title: "C&#243;mo: Implementar la palabra clave lock de C# (C++/CLI) | Microsoft Docs"
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
  - "lock (palabra clave) de C# [C++]"
  - "lock (instrucción)"
ms.assetid: 436fe544-ffb7-49b9-9798-90794e9974de
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Implementar la palabra clave lock de C# (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se muestra la forma de implementar en Visual C\+\+ la palabra clave `lock` de C\#.  Para obtener más información, vea [lock \(Instrucción\)](../Topic/lock%20Statement%20\(C%23%20Reference\).md).  
  
 También puede utilizar la clase `lock` de la Biblioteca de compatibilidad de C\+\+.  Para obtener más información, vea [Sincronización \(Clase lock\)](../dotnet/synchronization-lock-class.md).  
  
## Ejemplo  
  
```  
// CS_lock_in_CPP.cpp  
// compile with: /clr  
using namespace System::Threading;  
ref class Lock {  
   Object^ m_pObject;  
public:  
   Lock( Object ^ pObject ) : m_pObject( pObject ) {  
      Monitor::Enter( m_pObject );  
   }  
   ~Lock() {  
      Monitor::Exit( m_pObject );  
   }  
};  
  
ref struct LockHelper {  
   void DoSomething();  
};  
  
void LockHelper::DoSomething() {  
   // Note: Reference type with stack allocation semantics to provide   
   // deterministic finalization  
  
   Lock lock( this );     
   // LockHelper instance is locked  
}  
  
int main()  
{  
   LockHelper lockHelper;  
   lockHelper.DoSomething();  
   return 0;  
}  
```  
  
## Vea también  
 [Interoperabilidad con otros lenguajes de .NET](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)