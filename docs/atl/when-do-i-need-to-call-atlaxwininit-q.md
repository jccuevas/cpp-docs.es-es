---
title: "When Do I Need to Call AtlAxWinInit? | Microsoft Docs"
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
  - "AtlAxWinInit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AtlAxWinInit method"
ms.assetid: 080b9cfe-d85a-4439-a9e9-ab3966ebaa8e
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# When Do I Need to Call AtlAxWinInit?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[AtlAxWinInit](../Topic/AtlAxWinInit.md) registra la clase de ventana de **"AtlAxWin80"** \(más un par de mensajes personalizados de la ventana\) para que esta función debe llamar antes de intentar crear una ventana host.  Sin embargo, no siempre necesita llamar a esta función explícitamente, ya que las API de hospedaje \(y las clases que se utilizan\) llaman a menudo esta función para usted.  No hay ningún daño de llamar a esta función más de una vez.  Para obtener más información, vea [¿Cuál es el ATL API CONTROL\- De Hospedaje?](../atl/what-is-the-atl-control-hosting-api-q.md).  
  
## Vea también  
 [When Do I Need to Call AtlAxWinTerm?](../atl/when-do-i-need-to-call-atlaxwinterm-q.md)   
 [Preguntas más frecuentes sobre contención de controles](../atl/atl-control-containment-faq.md)