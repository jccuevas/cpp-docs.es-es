---
title: "Advertencia del compilador (nivel 3) C4398 | Microsoft Docs"
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
  - "C4398"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4398"
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 3) C4398
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable' : el objeto global por proceso no puede trabajar correctamente con varios AppDomains; utilice \_\_declspec\(dominio de aplicación\)  
  
 Una función virtual con convención de llamada [\_\_clrcall](../../cpp/clrcall.md) en un tipo nativo produce la creación de una vtable por dominio de aplicación.  Estas variables pueden no corregirse adecuadamente cuando se utilizan en varios dominios de aplicación.  
  
 Para resolverlo, compile con **\/clr:pure**, que, de manera predeterminada, hace variables globales por AppDomain, o marque explícitamente la variable `__declspec(appdomain)`.  
  
 Para obtener más información, vea [appdomain](../../cpp/appdomain.md) y [Dominios de aplicación y Visual C\+\+](../../dotnet/application-domains-and-visual-cpp.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4398.  
  
```  
// C4398.cpp  
// compile with: /clr /W3 /c  
struct S {  
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall  
};  
  
S glob_s;   // C4398  
__declspec(appdomain) S glob_s2;   // OK  
```