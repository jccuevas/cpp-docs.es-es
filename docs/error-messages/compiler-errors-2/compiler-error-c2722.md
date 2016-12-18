---
title: "Error del compilador C2722 | Microsoft Docs"
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
  - "C2722"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2722"
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2722
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'::operador' : elemento no válido después del comando de operadores; utilice el 'operator operador'  
  
 Una instrucción `operator` vuelve a definir `::new` o `::delete`.  Los operadores `new` y `delete` son globales, por lo que el operador de resolución de ámbito \(`::`\) no tiene sentido.  Quite el operador `::`.