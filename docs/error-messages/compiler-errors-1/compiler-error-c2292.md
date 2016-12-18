---
title: "Error del compilador C2292 | Microsoft Docs"
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
  - "C2292"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2292"
ms.assetid: 256b392f-2b8f-4162-b578-e7633984e162
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2292
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador': representación de herencia de mejor caso: se ha declarado 'representación1' pero se requiere 'representación2'  
  
 La compilación del siguiente código con [\/vmb](../../build/reference/vmb-vmg-representation-method.md) \(representación "mejor caso siempre"\) genera el error C2292.  
  
```  
// C2292.cpp  
// compile with: /vmb  
class __single_inheritance X;  
  
struct A { };  
struct B { };  
struct X : A, B { };  // C2292, X uses multiple inheritance  
```