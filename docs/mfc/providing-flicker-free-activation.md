---
title: "Proporcionar activaci&#243;n sin parpadeo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "activación [C++], sin parpadeo"
  - "parpadeo, controles ActiveX en MFC"
  - "controles ActiveX en MFC [C++], sin parpadeo"
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Proporcionar activaci&#243;n sin parpadeo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si el control se dibuja idéntica en los estados inactivas y activo \(y no utiliza la activación sin ventana\), puede eliminar las operaciones de dibujo y el parpadeo visual de acompañamiento que aparecen normalmente al crear la transición entre estados inactivas y activo.  Para ello, incluya la marca de **noFlickerActivate** en el conjunto de indicadores devueltos por [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md).  Por ejemplo:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/CPP/providing-flicker-free-activation_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/CPP/providing-flicker-free-activation_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/CPP/providing-flicker-free-activation_3.cpp)]  
  
 El código para incluir este marcador se genera automáticamente si selecciona la opción de **Flicker\-Free activation** en la página de [Configuración del control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) al crear el control con el asistente para controles ActiveX MFC.  
  
 Si utiliza la activación sin ventana, esta optimización no tiene ningún efecto.  
  
## Vea también  
 [Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)