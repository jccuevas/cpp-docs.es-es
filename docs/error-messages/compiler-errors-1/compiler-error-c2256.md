---
title: "Error del compilador C2256 | Microsoft Docs"
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
  - "C2256"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2256"
ms.assetid: 171fa2bc-8c72-49cd-afe5-d723b7acd3c5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2256
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

uso no válido de especificador friend en 'función'  
  
 No se puede especificar un destructor o un constructor como [friend](../../cpp/friend-cpp.md).  
  
 El código siguiente genera el error C2256:  
  
```  
// C2256.cpp  
// compile with: /c  
class C {  
public:  
   friend ~C();   // C2256  
   ~C();   // OK  
};  
```