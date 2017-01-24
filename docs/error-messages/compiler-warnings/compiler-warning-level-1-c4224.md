---
title: "Advertencia del compilador (nivel 1) C4224 | Microsoft Docs"
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
  - "C4224"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4224"
ms.assetid: 1531cae0-5040-49fd-b149-005bb5085391
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4224
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado una extensión no estándar : el parámetro formal 'identificador' se definió anteriormente como un tipo  
  
 El identificador se utilizó anteriormente como `typedef`.  Esto hace que se genere una advertencia cuando se habilita la compatibilidad con ANSI \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\).  
  
## Ejemplo  
  
```  
// C4224.cpp  
// compile with: /Za /W1 /LD  
typedef int I;  
void func ( int I );  // C4224  
```