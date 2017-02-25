---
title: "Error del compilador C3113 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3113"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3113"
ms.assetid: 3afdc668-b29e-474e-9ea3-aa027d42db7c
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C3113
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'estructura' no puede ser plantilla\/genérica  
  
 Se ha intentado crear una clase de plantilla o una clase genérica a partir de una interfaz o enumeración.  
  
 El código siguiente genera el error C3113:  
  
```  
// C3113.cpp  
// compile with: /c  
template <class T>   
enum E {};   // C3113  
// try the following line instead  
// class MyClass{};  
```