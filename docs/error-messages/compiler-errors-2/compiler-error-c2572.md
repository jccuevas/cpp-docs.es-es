---
title: "Error del compilador C2572 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2572"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2572"
ms.assetid: f1a42d69-727d-4ce5-88c8-d5f55dea66ac
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2572
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class::member' : redefinición de parámetro predeterminado : parámetro param  
  
 Los parámetros predeterminados no pueden definirse de nuevo.  Si requiere otro valor para el parámetro, debe dejarse sin definir el parámetro predeterminado.  
  
 El código siguiente genera el error C2572:  
  
```  
// C2572.cpp  
// compile with: /c  
void f(int i = 1);   // function declaration  
  
// function definition  
void f(int i = 1) {}   // C2572  
  
// try the following line instead  
// void f(int i) {}  
```