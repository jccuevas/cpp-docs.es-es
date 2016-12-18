---
title: "When Do I Need to Call AtlAxWinTerm? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AtlAxWinTerm"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AtlAxWinTerm method"
ms.assetid: 0088d494-2d8d-45b4-b582-2af726bd6cbd
caps.latest.revision: 12
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# When Do I Need to Call AtlAxWinTerm?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Anula de[AtlAxWinTerm](../Topic/AtlAxWinTerm.md) la clase de ventana de **"AtlAxWin80"** .  Se debe llamar a las ventanas hospedadas existentes de esta función \(si ya no es necesario crear para hospedar las ventanas\) después de todo se ha destruido.  Si no se llama a esta función, la clase de ventana no estará registrada automáticamente cuando el proceso finaliza.  
  
## Vea también  
 [When Do I Need to Call AtlAxWinInit?](../atl/when-do-i-need-to-call-atlaxwininit-q.md)   
 [Preguntas más frecuentes sobre contención de controles](../atl/atl-control-containment-faq.md)