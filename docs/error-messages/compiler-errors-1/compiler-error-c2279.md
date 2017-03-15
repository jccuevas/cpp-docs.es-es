---
title: "Error del compilador C2279 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2279"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2279"
ms.assetid: 1b5c88ef-2336-49b8-9ddb-d61f97c73e14
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C2279
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la especificación de la excepción no puede aparecer en una declaración de tipo typedef  
  
 Al utilizar **\/Za**, no se permite utilizar las [especificaciones de excepciones](../../cpp/exception-specifications-throw-cpp.md) en una declaración de tipo typedef.  
  
 El código siguiente genera el error C2279:  
  
```  
// C2279.cpp  
// compile with: /Za /c  
typedef int (*xy)() throw(...);   // C2279  
typedef int (*xyz)();   // OK  
```