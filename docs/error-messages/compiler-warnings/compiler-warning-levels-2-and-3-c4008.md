---
title: "Advertencia del compilador (niveles 2 y 3) C4008 | Microsoft Docs"
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
  - "C4008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4008"
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (niveles 2 y 3) C4008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador': atributo ' atributo ' omitido  
  
 El compilador omitió el atributo `__fastcall`, **estatic** o **inline** para una función \(advertencia de nivel 3\) o datos \(advertencia de nivel 2\).  
  
### Posibles causas del error:  
  
1.  El atributo `__fastcall` con datos.  
  
2.  Los atributos **static** o **inline** con la función **main**.