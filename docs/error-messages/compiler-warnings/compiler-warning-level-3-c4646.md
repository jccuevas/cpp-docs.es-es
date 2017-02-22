---
title: "Advertencia del compilador (nivel 3) C4646 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4646"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4646"
ms.assetid: 23677e8e-603e-40e0-b99a-2e4894a1278e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 3) C4646
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la función declarada con \_\_declspec\(noreturn\) tiene un tipo de valor devuelto distinto de void  
  
 Una función marcada con el modificador [noreturn](../../cpp/noreturn.md) `__declspec` debe tener un tipo de vuelto [void](../../cpp/void-cpp.md).  
  
 El ejemplo siguiente genera la advertencia C4646:  
  
```  
// C4646.cpp // compile with: /W3 /WX int __declspec(noreturn) TestFunction() {   // C4646  make return type void }  
```