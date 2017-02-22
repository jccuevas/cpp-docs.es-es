---
title: "Advertencia del compilador (nivel 4) C4125 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4125"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4125"
ms.assetid: a081d1f4-0789-4915-91df-7ff0b28ca245
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 4) C4125
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el dígito decimal finaliza la secuencia de escape octal  
  
 El compilador evalúa el número octal sin el dígito decimal y supone que el dígito decimal es un carácter.  
  
## Ejemplo  
  
```  
// C4125a.cpp // compile with: /W4 char array1[] = "\709"; // C4125 int main() { }  
```  
  
 Si el dígito 9 está pensado como un carácter, corrija el ejemplo siguiente:  
  
```  
// C4125b.cpp // compile with: /W4 char array[] = "\0709";  // C4125 String containing "89" int main() { }  
```