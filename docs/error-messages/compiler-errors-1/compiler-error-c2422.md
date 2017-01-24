---
title: "Error del compilador C2422 | Microsoft Docs"
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
  - "C2422"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2422"
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2422
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

reemplazo de segmento no válido en 'operando'  
  
 El código de ensamblado en línea utiliza incorrectamente un operador de reemplazo de segmento \(dos puntos\) en un operando.  Entre las posibles causas se incluyen:  
  
-   El registro que precede al operador no es un registro de segmento.  
  
-   El registro que precede al operador no es el único registro de segmento del operando.  
  
-   El operador de reemplazo de segmento aparece en un operador de direccionamiento indirecto \(paréntesis\).  
  
-   La expresión que sigue al operador de reemplazo de segmento no es un operando inmediato o un operando de memoria.  
  
 El código siguiente genera el error C2422:  
  
```  
// C2422.cpp  
// processor: x86  
int main() {  
   _asm {  
      mov AX, [BX:ES]   // C2422  
      mov AX, ES   // OK  
   }  
}  
```