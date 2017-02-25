---
title: "Error del compilador C3556 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3556"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3556"
ms.assetid: 9b002dcc-494e-414f-9587-20c2a0a39333
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3556
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'expresión': argumento incorrecto para 'decltype'  
  
 El compilador no puede deducir el tipo de la expresión que es el argumento para el especificador de tipo `decltype(``expression``)`. En el ejemplo de código siguiente, el compilador no puede deducir el tipo del argumento `myFunction` porque `myFunction` está sobrecargado.  
  
```  
void myFunction(); void myFunction(int); decltype(myFunction); // C3556  
```