---
title: "Advertencia del compilador (nivel 1) C4074 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4074"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4074"
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 1) C4074
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

inicializadores situados en el área de inicialización reservada para el compilador  
  
 El área de inicialización del compilador, que se especifica con la directiva [\#pragma init\_seg](../../preprocessor/init-seg.md), está reservada por Microsoft.  El código de esta área puede ejecutarse antes de inicializarse la biblioteca en tiempo de ejecución de C.  
  
 El código siguiente genera el error C4074:  
  
```  
// C4074.cpp  
// compile with: /W1  
#pragma init_seg( compiler )   // C4074  
  
// try this line to resolve the warning  
// #pragma init_seg(user)  
  
int main() {  
}  
```