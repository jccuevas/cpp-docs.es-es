---
title: "Error del compilador C2516 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2516"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2516"
ms.assetid: cd3accc1-0179-4a13-9587-616908c4ad1d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2516
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'nombre' : no es una clase base válida  
  
 La clase se deriva de un nombre de tipo definido por una instrucción `typedef`.  
  
 El código siguiente genera el error C2516:  
  
```  
// C2516.cpp  
typedef unsigned long ulong;  
class C : public ulong {}; // C2516  
```