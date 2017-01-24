---
title: "Error del compilador C2506 | Microsoft Docs"
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
  - "C2506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2506"
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2506
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'miembro' : '\_\_declspec\(modificador\)' no se puede aplicar a este símbolo  
  
 No puede declarar miembros estáticos de una clase administrada por proceso o por AppDomain.  
  
 Para obtener más información, vea [appdomain](../../cpp/appdomain.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2506.  
  
```  
// C2506.cpp  
// compile with: /clr /c  
ref struct R {  
   __declspec(process) static int n;   // C2506  
   int o;   // OK  
};  
```