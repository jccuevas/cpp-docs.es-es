---
title: "Advertencia del compilador (nivel 1) C4401 | Microsoft Docs"
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
  - "C4401"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4401"
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4401
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'campodebits' : el miembro es un campo de bits  
  
 El código de ensamblado en línea intenta obtener acceso a un miembro de campo de bits.  El ensamblado en línea no puede obtener acceso a los miembros de campo de bits, por lo que se utiliza el último límite de empaquetado antes de usar el miembro de campo de bits.  
  
 Para evitar esta advertencia, convierta el tipo del campo de bits en el tipo adecuado antes de crear la referencia en el código de ensamblado en línea.  El código siguiente genera el error C4401:  
  
```  
// C4401.cpp  
// compile with: /W1  
// processor: x86  
typedef struct bitfield {  
   signed bit : 1;  
} mybitfield;  
  
int main() {  
   mybitfield bf;  
   bf.bit = 0;  
   __asm {  
      mov bf.bit,0;   // C4401  
   }  
  
   /* use the following __asm block to resolve the warning  
   int i = (int)bf.bit;  
   __asm {  
      mov i,0;  
   }  
   */  
}  
```