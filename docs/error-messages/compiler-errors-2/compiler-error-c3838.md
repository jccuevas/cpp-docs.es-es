---
title: "Error del compilador C3838 | Microsoft Docs"
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
  - "C3838"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3838"
ms.assetid: d6f470c2-131a-4a8c-843a-254acd43da83
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3838
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede heredar explícitamente de 'tipo'  
  
 El `type` especificado no puede actuar como clase base de ninguna clase.  
  
 El código siguiente genera el error C3838:  
  
```  
// C3838a.cpp  
// compile with: /clr /c  
public ref class B : public System::Enum {};   // C3838  
```  
  
 El código siguiente genera el error C3838:  
  
```  
// C3838b.cpp  
// compile with: /clr:oldSyntax /c  
public __gc class B : public System::ValueType {};   // C3838  
```