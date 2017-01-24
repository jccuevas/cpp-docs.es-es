---
title: "Error del compilador C2360 | Microsoft Docs"
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
  - "C2360"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2360"
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2360
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la inicialización de 'identifier' se omite en la etiqueta 'case'  
  
 La inicialización de `identifier` se puede omitir en una instrucción `switch`.  No se puede omitir una declaración con un inicializador a menos que esté contenida dentro de un bloque. A menos que se declare en un bloque, la variable queda dentro del ámbito hasta el final de la instrucción `switch`.  
  
 El código siguiente genera el error C2360:  
  
```  
// C2360.cpp  
int main() {  
   int x = 0;  
   switch ( x ) {  
   case 0 :  
      int i = 1;  
      { int j = 1; }  
   case 1 :   // C2360  
      int k = 1;  
   }  
}  
```  
  
 Posible solución:  
  
```  
// C2360b.cpp  
int main() {  
   int x = 0;  
   switch ( x ) {  
   case 0 :  
      { int j = 1; int i = 1;}  
   case 1 :  
      int k = 1;  
   }  
}  
```