---
title: "Advertencia del compilador (nivel 1) C4090 | Microsoft Docs"
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
  - "C4090"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4090"
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4090
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operación' : calificadores 'modificador' diferentes  
  
 Una variable usada en una operación se definió con un modificador especificado que impide que el compilador la modifique sin detectarse.  Se compiló la expresión sin modificaciones.  
  
 Esta advertencia puede aparecer cuando un puntero a un elemento **const** o `volatile` se asigna a un puntero no declarado como puntero a **const** o `volatile`.  
  
 Esta advertencia se emite para programas en C.  En un programa en C\+\+, el compilador emite un error: [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).  
  
 El código siguiente genera el error C4090:  
  
```  
// C4090.c  
// compile with: /W1  
int *volatile *p;  
int *const *q;  
int **r;  
  
int main() {  
   p = q;   // C4090  
   p = r;  
   q = p;   // C4090  
   q = r;  
   r = p;   // C4090  
   r = q;   // C4090  
}  
```