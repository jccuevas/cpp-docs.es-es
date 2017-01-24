---
title: "Can I Reuse a Host Window? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "host windows"
ms.assetid: bcd08ab1-cfcf-49e3-b4e8-ac134d141005
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Can I Reuse a Host Window?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

No se recomienda reutiliza las ventanas del host.  Para garantizar la solidez del código, debe asociar la duración de la ventana host a la duración de un único control.  
  
## Vea también  
 [Preguntas más frecuentes sobre contención de controles](../atl/atl-control-containment-faq.md)