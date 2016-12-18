---
title: "Error del compilador C3050 | Microsoft Docs"
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
  - "C3050"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3050"
ms.assetid: ee090a0b-29cc-4215-a2f9-d82af79b8e82
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3050
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type1': una clase ref no puede heredar de 'type1'  
  
 `System::ValueType` no puede ser una clase base para un tipo de referencia.  
  
 El ejemplo siguiente genera la advertencia C3050:  
  
```  
// C3050.cpp // compile with: /clr /LD ref struct X : System::ValueType {};   // C3050 ref struct Y {};   // OK  
```