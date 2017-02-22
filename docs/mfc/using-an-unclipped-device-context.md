---
title: "Usar un contexto de dispositivo no recortado | Microsoft Docs"
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
  - "controles ActiveX en MFC, contexto de dispositivo no recortado"
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Usar un contexto de dispositivo no recortado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si está totalmente seguro que el control no pintar fuera del rectángulo del cliente, puede realizar un aumento pequeño pero detectable de velocidad deshabilitando la llamada a `IntersectClipRect` que hace por `COleControl`.  Para ello, quite la marca de **clipPaintDC** del conjunto de indicadores devueltos por [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md).  Por ejemplo:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/CPP/using-an-unclipped-device-context_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/CPP/using-an-unclipped-device-context_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/CPP/using-an-unclipped-device-context_3.cpp)]  
  
 El código para quitar este marcador se genera automáticamente si selecciona la opción de **Unclipped Device Context** en la página de [Configuración del control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) , al crear el control con el asistente para controles ActiveX MFC.  
  
 Si utiliza la activación sin ventana, esta optimización no tiene ningún efecto.  
  
## Vea también  
 [Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)