---
title: "Advertencia del compilador (nivel 1) C4020 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4020"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4020"
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 1) C4020
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : hay demasiados parámetros reales  
  
 El número de parámetros reales de una llamada de función supera el número de parámetros formales del prototipo o definición de función.  El compilador pasa los parámetros reales adicionales según la convención de llamada de la función.  
  
 El código siguiente genera el error C4020:  
  
```  
// C4020.c  
// compile with: /W1 /c  
void f(int);  
int main() {  
   f(1,2);   // C4020  
}  
```  
  
 Posible solución:  
  
```  
// C4020b.c  
// compile with: /c  
void f(int);  
int main() {  
   f(1);  
}  
```