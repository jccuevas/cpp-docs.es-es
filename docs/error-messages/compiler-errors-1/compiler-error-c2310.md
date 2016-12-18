---
title: "Error del compilador C2310 | Microsoft Docs"
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
  - "C2310"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2310"
ms.assetid: 1969c682-b97e-43fb-b9a9-f783e7ff1710
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2310
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

los controladores de tipo catch deben especificar un tipo  
  
 El controlador catch especificado no tiene tipo o tiene varios tipos.  
  
 El código siguiente genera el error C2310:  
  
```  
// C2310.cpp  
// compile with: /EHsc  
#include <eh.h>  
int main() {  
   try {  
      throw "Out of memory!";  
   }  
   catch( int ,int) {}   // C2310 two types  
   // try the following line instead  
   // catch( int)  {}  
}  
```