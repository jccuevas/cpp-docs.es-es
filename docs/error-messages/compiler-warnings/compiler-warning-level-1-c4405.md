---
title: "Advertencia del compilador (nivel 1) C4405 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4405"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4405"
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4405
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : el identificador es una palabra reservada  
  
 Una palabra reservada para el ensamblado en línea se utiliza como nombre de variable.  Esto puede causar resultados imprevisibles.  Para corregir esta advertencia, evite dar a las variables nombres que contengan palabras reservadas para el ensamblado en línea.  El código siguiente genera el error C4405:  
  
```  
// C4405.cpp  
// compile with: /W1  
// processor: x86  
void func1() {  
   int mov = 0, i = 0;  
   _asm {  
      mov mov, 0;   // C4405  
      // instead, try ..  
      // mov i, 0;  
   }  
}  
  
int main() {  
}  
```