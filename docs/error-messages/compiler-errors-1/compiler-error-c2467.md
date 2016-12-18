---
title: "Error del compilador C2467 | Microsoft Docs"
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
  - "C2467"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2467"
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2467
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

declaración no válida de 'tipo\-definido\-por\-el\-usuario' anónimo  
  
 Se ha declarado un tipo definido por el usuario anidado.  Esto es un error al compilar código fuente C con la opción de compatibilidad ANSI habilitada \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\).  
  
 El código siguiente genera el error C2467:  
  
```  
//C2467.c  
// compile with: /Za   
int main() {  
   struct X {  
      union { int i; };   // C2467, nested declaration  
   };  
}  
```