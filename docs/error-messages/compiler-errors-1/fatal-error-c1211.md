---
title: "Error irrecuperable C1211 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1211"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1211"
ms.assetid: df0ca70d-ec6e-4400-926a-b877e2599978
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Error irrecuperable C1211
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La versión del runtime instalada no admite el atributo personalizado TypeForwardedTo  
  
 El error C1211 se produce cuando tiene un compilador para la versión actual, pero un Common Language Runtime de una versión anterior.  
  
 Parte de la funcionalidad del compilador podría no funcionar en una versión anterior de runtime.  
  
 Para resolver el error C1211, instale el Common Language Runtime que se incluye con el compilador que está usando.  
  
 Para obtener más información, consulta [Reenvío de tipos \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md).