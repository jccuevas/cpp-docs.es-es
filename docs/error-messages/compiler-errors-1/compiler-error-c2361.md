---
title: "Error del compilador C2361 | Microsoft Docs"
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
  - "C2361"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2361"
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2361
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la inicialización de 'identificador' se omite en la etiqueta 'default'  
  
 La inicialización de `identifier` se puede omitir en una instrucción `switch`.  No se puede omitir una declaración con un inicializador a menos que esté contenida dentro de un bloque. A menos que se declare en un bloque, la variable queda dentro del ámbito hasta el final de la instrucción `switch`.  
  
 El código siguiente genera el error C2361:  
  
```  
// C2361.cpp  
void func( void ) {  
   int x;  
   switch (x) {  
   case 0 :  
      int i = 1;  
      { int j = 1; }  
   default :   // C2361 error  
      int k = 1;  
   }  
}  
```  
  
 Posible solución:  
  
```  
// C2361b.cpp  
// compile with: /c  
void func( void ) {  
   int x = 0;  
   switch (x) {  
   case 0 :  
      { int j = 1; int i = 1;}  
   default :  
      int k = 1;  
   }  
}  
```