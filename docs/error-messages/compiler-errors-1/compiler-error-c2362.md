---
title: "Error del compilador C2362 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2362"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2362"
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2362
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la inicialización de 'identificador' se omite en 'goto etiqueta'  
  
 Al compilar con [\/Za](../../build/reference/za-ze-disable-language-extensions.md), saltar a la etiqueta impide que se inicialice el identificador.  
  
 No se puede saltar por encima de una declaración que contenga un inicializador a menos que la declaración esté contenida en un bloque que no se procesa, o a menos que ya esté inicializada la variable.  
  
 El código siguiente genera el error C2326:  
  
```  
// C2362.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   int i = 1;      // C2362, initialization skipped  
label1:;  
}  
```  
  
 Posible solución:  
  
```  
// C2362b.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   {  
      int j = 1;   // OK, this block is never entered  
   }  
label1:;  
}  
```