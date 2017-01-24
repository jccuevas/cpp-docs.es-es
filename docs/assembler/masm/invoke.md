---
title: "INVOKE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Invoke"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "INVOKE directive"
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# INVOKE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Llama al procedimiento en la dirección especificada por *la expresión*, pasando los argumentos en la pila o en registros según las convenciones de llamada estándar de tipo de lenguaje.  
  
## Sintaxis  
  
```  
  
INVOKE   
expression [[, arguments]]  
```  
  
## Comentarios  
 Cada argumento transferido al procedimiento puede ser una expresión, un par de registro, o una expresión de dirección \(una expresión precedida por `ADDR`\).  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)