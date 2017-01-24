---
title: "Error del compilador C2008 | Microsoft Docs"
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
  - "C2008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2008"
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'carácter' : no se esperaba en la definición de macro  
  
 Hay un carácter inmediatamente después del nombre de la macro.  Para resolver el error, deje un espacio después del nombre de la macro.  
  
 El código siguiente genera el error C2008:  
  
```  
// C2008.cpp  
#define TEST1"mytest1"    // C2008  
```  
  
 Posible solución:  
  
```  
// C2008b.cpp  
// compile with: /c  
#define TEST2 "mytest2"  
```