---
title: "Error del compilador C3354 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3354"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3354"
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C3354
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': la función usada para crear un delegado no puede tener el tipo de valor devuelto 'type'  
  
 Los tipos siguientes no son válidos como tipos de valor devuelto para un [delegado](../../misc/delegate.md):  
  
-   De puntero a función  
  
-   Puntero a miembro  
  
-   Puntero a función miembro  
  
-   Referencia a función  
  
-   Referencia a función miembro  
  
 El ejemplo siguiente genera la advertencia C3354:  
  
```  
// C3354_2.cpp // compile with: /clr /c using namespace System; typedef void ( *VoidPfn )(); delegate VoidPfn func(); // C3354 // try the following line instead // delegate  void func();  
```  
  
 El ejemplo siguiente genera la advertencia C3354:  
  
```  
// C3354.cpp // compile with: /clr:oldSyntax /c #using <mscorlib.dll> using namespace System; typedef void (*VoidPfn)(); __delegate VoidPfn func();   // C3354 // try the following line instead // __delegate void func();  
```