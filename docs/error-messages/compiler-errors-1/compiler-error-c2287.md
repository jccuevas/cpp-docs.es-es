---
title: "Error del compilador C2287 | Microsoft Docs"
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
  - "C2287"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2287"
ms.assetid: 64556299-4e1f-4437-88b7-2464fc0b95bb
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2287
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase': representación de herencia: 'representación1' es menos general que la representación 'representación2' requerida  
  
 Se ha declarado una clase con una representación más sencilla que la requerida.  
  
 El código siguiente genera el error C2287:  
  
```  
// C2287.cpp  
// compile with: /vmg /c  
class __single_inheritance X;  
class __single_inheritance Y;  
  
struct A { };  
struct B { };  
struct X : A, B { };  // C2287  X uses multiple inheritance  
struct Y : A { };  // OK  
```