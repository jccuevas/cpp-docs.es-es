---
title: "Error del compilador C3625 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3625"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3625"
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C3625
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'native\_type': un tipo nativo no puede derivar de un tipo administrado o WinRT 'type'  
  
 Una clase nativa no puede heredarse de una clase administrada o WinRT.  Para obtener más información, vea [Clases y structs](../../windows/classes-and-structs-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera el error C3625:  
  
```  
// C3625.cpp  
// compile with: /clr /c  
ref class B {};  
class D : public B {};   // C3625 cannot inherit from a managed class  
```  
  
 El ejemplo siguiente genera el error C3625:  
  
```  
// C3625_b.cpp  
// compile with: /clr:oldSyntax /c  
__gc class B {};  
class D : public B {};   // C3625  cannot inherit from a managed class  
```