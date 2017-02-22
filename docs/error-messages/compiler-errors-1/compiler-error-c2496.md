---
title: "Error del compilador C2496 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2496"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2496"
ms.assetid: 9a25237d-5bbb-4112-98f3-29cd99d3f89f
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2496
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : 'selectany' sólo se puede aplicar a elementos de datos con vinculación externa  
  
 El atributo [selectany](../../cpp/selectany.md) sólo se puede aplicar a elementos de datos globales y visibles externamente.  
  
 El código siguiente genera el error C2496:  
  
```  
// C2496.cpp  
// compile with: /c  
__declspec(selectany) int x1 = 1;  
const __declspec(selectany) int x2 = 2;   // C2496  
static __declspec(selectany) int x6 = 6;   // C2496  
  
extern const __declspec(selectany) int x3 = 3;  
  
__declspec(selectany) int x4;  
  
// dynamic initialization of x5  
int f();  
__declspec(selectany) int x5 = f();  
  
extern const int x7;  
// OK - redeclaration of x7 that is extern  
const __declspec(selectany) int x7 = 7;  
```