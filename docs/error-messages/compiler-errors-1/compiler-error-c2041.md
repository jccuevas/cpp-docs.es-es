---
title: "Error del compilador C2041 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2041"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2041"
ms.assetid: c9a33bb1-f9cf-47d6-bd21-7d867a8c37d5
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2041
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

dígito 'carácter' no válido para la base 'número'  
  
 El carácter especificado no es un dígito válido para la base \(octal o hexadecimal\).  
  
 El código siguiente genera el error C2041:  
  
```  
// C2041.cpp  
int i = 081;   // C2041  8 is not a base 8 digit  
```  
  
 Posible solución:  
  
```  
// C2041b.cpp  
// compile with: /c  
int j = 071;  
```