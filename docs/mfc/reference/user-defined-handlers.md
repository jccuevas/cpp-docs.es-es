---
title: "Controladores definidos por el usuario | Microsoft Docs"
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
  - "vc.mfc.handlers"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_MESSAGE (macro)"
  - "ON_REGISTERED_MESSAGE (macro)"
  - "controladores definidos por el usuario"
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controladores definidos por el usuario
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las entradas de mapa siguiente corresponden a los prototipos de función.  
  
|Entrada de asignación|Prototipo de función|  
|---------------------------|--------------------------|  
|ON\_MESSAGE \( \<mensaje\>, \<memberFxn\> \)|memberFxn de afx\_msg LRESULT \(WPARAM, LPARAM\);|  
|ON\_REGISTERED\_MESSAGE \( \<nMessageVariable\>, \<memberFxn\> \)|memberFxn de afx\_msg LRESULT \(WPARAM, LPARAM\);|  
|ON\_THREAD\_MESSAGE \( \<mensaje\>, \<memberFxn\> \)|memberFxn vacío de afx\_msg \(WPARAM, LPARAM\);|  
|ON\_REGISTERED\_THREAD\_MESSAGE \( \<nMessageVariable\>, \<memberFxn\> \)|memberFxn vacío de afx\_msg \(WPARAM, LPARAM\);|  
  
## Vea también  
 [Mapas de mensajes](../../mfc/reference/message-maps-mfc.md)   
 [Controladores de mensajes WM\_](../../mfc/reference/handlers-for-wm-messages.md)