---
title: "Error irrecuperable C1045 | Microsoft Docs"
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
  - "C1045"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1045"
ms.assetid: 766c2f89-4ecd-4281-adaa-14b270cc0829
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1045
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

límite del compilador : las especificaciones de vinculación están demasiado anidadas  
  
 Los externos anidados superan el límite del compilador. Se permiten los externos anidados con el tipo de vinculación externa, como `extern` "C\+\+". Reduzca el número de externos anidados para resolver el error.