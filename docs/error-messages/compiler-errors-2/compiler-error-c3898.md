---
title: "Error del compilador C3898 | Microsoft Docs"
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
  - "C3898"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3898"
ms.assetid: d9a90df6-87e4-4fe7-ab01-c226ee86bf10
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3898
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : los miembros de datos de tipo solamente pueden ser miembros de tipos administrados  
  
 Se declaró un miembro de datos [initonly](../../dotnet/initonly-cpp-cli.md) en una clase nativa.  Un miembro de datos `initonly` sólo se puede declarar en una clase CLR.  
  
 El código siguiente genera el error C3898:  
  
```  
// C3898.cpp  
// compile with: /clr  
struct Y1 {  
   initonly  
   static int data_var = 9;   // C3898  
};  
```  
  
 Posible solución:  
  
```  
// C3898b.cpp  
// compile with: /clr /c  
ref struct Y1 {  
   initonly  
   static int data_var = 9;  
};  
```