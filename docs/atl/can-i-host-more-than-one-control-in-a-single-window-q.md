---
title: "Can I Host More Than One Control in a Single Window? | Microsoft Docs"
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
  - "controles [ATL], hosting multiple"
  - "windows [C++], hosting multiple controls"
ms.assetid: 3a967a1a-7e7e-42e3-8eed-f7bde912363f
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Can I Host More Than One Control in a Single Window?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

No es posible hospedar más de un control en una sola ventana host ATL.  Cada ventana hospedada está diseñado para contener exactamente un control al mismo tiempo \(esto permite un mecanismo simple para administrar la reflexión de mensaje y propiedades de ambiente de la por\- CONTROL\).  Sin embargo, si necesita al usuario ver varios controles en una sola ventana, es algo fácil crear ventanas host se crean como elementos secundarios de esa ventana.  
  
## Vea también  
 [Preguntas más frecuentes sobre contención de controles](../atl/atl-control-containment-faq.md)