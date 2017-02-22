---
title: "Error del compilador C2821 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2821"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2821"
ms.assetid: e8d71988-a968-4484-94db-e8c3bad74a4a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2821
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el primer parámetro formal para 'operator new' debe ser 'unsigned int'  
  
 El primer parámetro formal del [operator new](../Topic/operator%20new%20\(%3Cnew%3E\).md) debe ser `int` sin signo.  
  
 El código siguiente genera el error C2821:  
  
```  
// C2821.cpp  
// compile with: /c  
void * operator new( /* unsigned int,*/ void * );   // C2821  
void * operator new( unsigned int, void * );  
```