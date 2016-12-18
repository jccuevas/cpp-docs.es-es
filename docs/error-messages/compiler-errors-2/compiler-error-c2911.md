---
title: "Error del compilador C2911 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2911"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2911"
ms.assetid: 83c7c01a-ab6a-4179-9fb0-289a9ec8d44e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2911
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member': no se puede declarar ni definir en el ámbito actual  
  
 Dentro de un espacio de nombres, una clase o una función, solo se puede definir un miembro del mismo espacio de nombres, la misma clase o la misma función, o bien un miembro que esté incluido en estos.  
  
 El ejemplo siguiente genera la advertencia C2911:  
  
```  
// C2911.cpp struct A; namespace M { struct D; } namespace N { struct C; namespace O { struct B; } // in N struct ::A {};   // C2911  A is member of global NS struct O::B{};   // OK B is in O, O is inside of N struct C {};     // OK C is member of N struct M::D {};  // C2911 D is member of M, M not enclosed by N }  
```