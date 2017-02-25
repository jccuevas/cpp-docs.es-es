---
title: "Error del compilador C2208 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2208"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2208"
ms.assetid: 9ae704bc-bf70-45f1-8e47-0470f21edd4e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2208
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo' : no se han definido miembros utilizando este tipo  
  
 Un identificador que se resuelve con un nombre de tipo está en una declaración agregada, pero el compilador no puede declarar un miembro.  
  
 El código siguiente genera el error C2208:  
  
```  
// C2208.cpp  
class C {  
   C;   // C2208  
   C(){}   // OK  
};  
```