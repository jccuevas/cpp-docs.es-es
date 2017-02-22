---
title: "Advertencia del compilador (nivel 1) C4558 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4558"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4558"
ms.assetid: 52bb0324-7bec-468c-b35b-13a08d38e578
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4558
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el valor del operando 'valor' está fuera del intervalo 'límite inferior \- límite superior'  
  
 El valor pasado a una instrucción en lenguaje de ensamblado está fuera del intervalo especificado para el parámetro.  El valor quedará truncado.  
  
 El código siguiente genera el error C4558:  
  
```  
// C4558.cpp  
// compile with: /W1  
// processor: x86  
void asm_test() {  
   __asm pinsrw   mm1, eax, 8;   // C4558  
}  
  
int main() {  
}  
```