---
title: "Error irrecuperable C1210 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1210"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1210"
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error irrecuperable C1210
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La versión del runtime instalada no admite \/clr:pure ni \/clr:safe  
  
 El error C1210 se produce cuando tiene un compilador para la versión actual, pero un Common Language Runtime de una versión anterior.  
  
 Parte de la funcionalidad del compilador podría no funcionar en una versión anterior de runtime.  
  
 Para solucionar el error C1210, instale la versión de Common Language Runtime pensada para su uso con el compilador.