---
title: "Error del compilador C2561 | Microsoft Docs"
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
  - "C2561"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2561"
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2561
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : la función debe devolver un valor  
  
 Se declaró la función como si devolviera un valor, pero la definición de la función no contiene una instrucción `return`.  
  
 La causa de este error puede ser un prototipo de función incorrecto:  
  
1.  Si la función no devuelve un valor, declare la función con el tipo de valor devuelto [void](../../cpp/void-cpp.md).  
  
2.  Compruebe que todas las bifurcaciones posibles de la función devuelven un valor del tipo declarado en el prototipo.  
  
3.  Las funciones de C\+\+ que contienen rutinas de ensamblado en línea que almacenan el valor devuelto en el registro `AX` pueden requerir una instrucción return.  Copie el valor de `AX` en una variable temporal y haga que la función devuelva esa variable.  
  
 El código siguiente genera el error C2561:  
  
```  
// C2561.cpp  
int Test(int x) {  
   if (x) {  
      return;   // C2561  
      // try the following line instead  
      // return 1;  
   }  
   return 0;  
}  
  
int main() {  
   Test(1);  
}  
```