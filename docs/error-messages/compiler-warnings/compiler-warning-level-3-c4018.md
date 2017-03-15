---
title: "Advertencia del compilador (nivel 3) C4018 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4018"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4018"
ms.assetid: 6e8cbb04-d914-4319-b431-cbc2fbe40eb1
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 3) C4018
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'expresión' : no coinciden signed\/unsigned  
  
 La comparación de un número signed y otro unsigned requirió que el compilador convirtiera el valor signed en unsigned.  
  
 Se puede corregir esta advertencia si se convierte uno de los dos tipos al probar los tipos signed y unsigned.  
  
 El código siguiente genera el error C4018:  
  
```  
// C4018.cpp  
// compile with: /W3  
int main() {  
   unsigned int uc = 0;  
   int c = 0;  
   unsigned int c2 = 0;  
  
   if (uc < c) uc = 0;   // C4018  
  
   // OK  
   if (uc == c2) uc = 0;  
}  
```