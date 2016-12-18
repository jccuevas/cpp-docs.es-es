---
title: "Error del compilador C3279 | Microsoft Docs"
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
  - "C3279"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3279"
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3279
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se permiten especializaciones parciales o explícitas ni creaciones de instancias explícitas de plantillas de clase declaradas en el espacio de nombres cli  
  
 El espacio de nombres `cli` está definido por Microsoft y contiene pseudoplantillas. El compilador de Visual C\+\+ no permite las especializaciones definidas por el usuario, parciales, explícitas ni creaciones de instancias explícitas de plantillas de clase en este espacio de nombres.  
  
 El ejemplo siguiente genera la advertencia C3279:  
  
```  
// C3279.cpp // compile with: /clr namespace cli { template <> ref class array<int> {};   // C3279 template <typename T> ref class array<T, 2> {};   // C3279 }  
```