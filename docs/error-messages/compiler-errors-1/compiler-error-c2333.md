---
title: "Error del compilador C2333 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2333"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2333"
ms.assetid: 2636fc1e-d3e7-4e68-8628-3c81a99ba813
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2333
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : error en la declaración de función; se pasará por alto el cuerpo de la función  
  
 Este error se produce después de otro error, para las funciones miembro definidas dentro de su clase.  
  
 El código siguiente genera el error C2333:  
  
```  
// C2333.cpp  
struct s1 {  
   s1(s1) {}   // C2333  
};  
```