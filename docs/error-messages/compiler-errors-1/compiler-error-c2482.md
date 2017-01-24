---
title: "Error del compilador C2482 | Microsoft Docs"
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
  - "C2482"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2482"
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2482
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : no se permite la inicialización dinámica de datos 'thread'  
  
 Las variables declaradas con el atributo `thread` no se pueden inicializar con una expresión que requiera evaluación en tiempo de ejecución.  Se requiere una expresión estática para inicializar datos `thread`.  
  
 El código siguiente genera el error C2482:  
  
```  
// C2482.cpp  
// compile with: /c  
#define Thread __declspec( thread )  
Thread int tls_i = tls_i;   // C2482  
  
int j = j;   // OK in C++; C error  
Thread int tls_i = sizeof( tls_i );   // Okay in C and C++  
```