---
title: "Error del compilador C2483 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2483"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2483"
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C2483
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : el objeto con constructor o destructor no se puede declarar como 'thread'  
  
 Las variables declaradas con el atributo `thread` no se pueden inicializar con un constructor u otra expresión que requiera evaluación en tiempo de ejecución.  Se requiere una expresión estática para inicializar datos `thread`.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2483.  
  
```  
// C2483.cpp  
// compile with: /c  
__declspec(thread) struct A {  
   A(){}  
   ~A(){}  
} aa;   // C2483 error  
  
__declspec(thread) struct B {} b;   // OK  
```  
  
## Vea también  
 [subproceso](../../cpp/thread.md)