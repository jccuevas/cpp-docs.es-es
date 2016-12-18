---
title: "Advertencia del compilador (nivel 1) C4947 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4947"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4947"
ms.assetid: 5a1d484e-b4c7-4de2-a145-d8dcfc2fc1d2
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4947
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo\_o\_miembro': marcado como obsoleto  
  
 Un miembro o un tipo se marcó como obsoleto con la clase [ObsoleteAttribute](frlrfSystemObsoleteAttributeClassTopic).  
  
 El ejemplo siguiente genera la advertencia C4947:  
  
```  
// C4947.cpp // compile with: /clr /W1 // C4947 expected using namespace System; [System::ObsoleteAttribute] ref struct S { [System::ObsoleteAttribute] int i; [System::ObsoleteAttribute] void mFunc(){} }; // Any reference to Func1 should generate a warning [System::ObsoleteAttribute] Int32 Func1(Int32 a, Int32 b) { return (a + b); } // Any reference to Func2 should generate a warning with  message [System::ObsoleteAttribute("Will be removed in next version")] Int32 Func2(Int32 a, Int32 b) { return (a + b); } int main() { Int32 MyInt1 = ::Func1(2, 2); Int32 MyInt2 = ::Func2(2, 2); S^ s = gcnew S(); s->i = 10; s->mFunc(); }  
```