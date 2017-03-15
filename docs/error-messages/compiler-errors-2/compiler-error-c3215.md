---
title: "Error del compilador C3215 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3215"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3215"
ms.assetid: d0d16007-8885-42e0-b086-2d3a61f348c5
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C3215
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type1': el parámetro de tipo genérico ya estaba restringido por 'type2'  
  
 Se especificó una restricción más de una vez.  
  
 Para más información sobre genéricos, vea [Genéricos](../../windows/generics-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera la advertencia C3215:  
  
```  
// C3215.cpp // compile with: /clr interface struct A {}; generic <class T> where T : A,A ref class C {};   // C3215  
```  
  
 Posible solución:  
  
```  
// C3215b.cpp // compile with: /clr /c interface struct A {}; generic <class T> where T : A ref class C {};  
```