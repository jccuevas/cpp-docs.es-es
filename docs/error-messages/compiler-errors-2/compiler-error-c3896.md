---
title: "Error del compilador C3896 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3896"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3896"
ms.assetid: eb8be0f6-5b4e-4d71-8285-8a2a94f8ba29
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3896
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'miembro' : inicializador inadecuado: este miembro de datos literal solamente se puede inicializar con 'nullptr'  
  
 Se inicializó incorrectamente un miembro de datos [literal](../../windows/literal-cpp-component-extensions.md).  Para obtener más información, vea [nullptr](../../windows/nullptr-cpp-component-extensions.md).  
  
 El código siguiente genera el error C3896:  
  
```  
// C3896.cpp  
// compile with: /clr /c  
ref class R{};  
  
value class V {  
   literal R ^ r = "test";   // C3896  
   literal R ^ r2 = nullptr;   // OK  
};  
```