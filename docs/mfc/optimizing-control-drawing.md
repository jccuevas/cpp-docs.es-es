---
title: "Optimizar el dibujo de controles | Microsoft Docs"
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
  - "controles ActiveX en MFC, optimizar"
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Optimizar el dibujo de controles
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando un control se indica para dibujarse a sí mismo en un contexto contenedor\- proporcionado de dispositivo, selecciona normalmente los objetos GDI \(como lápices, pinceles, y proporciona\) en el contexto de dispositivo, realiza las operaciones de dibujo, y restaura los objetos anteriores de GDI.  Si el contenedor tiene varios controles que deben ser dibujados dentro del mismo contexto de dispositivo, y cada control selecciona los objetos GDI que requiere, tiempo puede guardarse si los controles no restablece individualmente objetos seleccionada anteriormente.  Después de que todos los controles se hayan dibujado, el contenedor automáticamente pueden restaurar los objetos originales.  
  
 Para detectar si un contenedor admite esta técnica, un control puede llamar a la función miembro de [COleControl::IsOptimizedDraw](../Topic/COleControl::IsOptimizedDraw.md) .  Si esta función devuelve **VERDADERO**, el control puede omitir el paso normal de restaurar los objetos seleccionada anteriormente.  
  
 Considere un control con la función \(no optimizado\) siguiente de `OnDraw` :  
  
 [!code-cpp[NVC_MFC_AxOpt#15](../mfc/codesnippet/CPP/optimizing-control-drawing_1.cpp)]  
  
 El lápiz y el pincel de este ejemplo son variables locales, lo que significa que los destructores se llamará cuando salen del ámbito \(cuando finaliza la función de `OnDraw` \).  Los destructores intentará eliminar los objetos correspondientes de GDI.  Pero no deben eliminarse si piensa dejarlos seleccionados en el contexto de dispositivo sobre volver de `OnDraw`.  
  
 Para evitar que los objetos de [CPen](../mfc/reference/cpen-class.md) y de [CBrush](../mfc/reference/cbrush-class.md) son destruidos cuando `OnDraw` finaliza, almacénelos en variables miembro en lugar de variables locales.  En la declaración de clase del control, agregue las declaraciones de dos nuevas variables miembro:  
  
 [!code-cpp[NVC_MFC_AxOpt#16](../mfc/codesnippet/CPP/optimizing-control-drawing_2.h)]  
[!code-cpp[NVC_MFC_AxOpt#17](../mfc/codesnippet/CPP/optimizing-control-drawing_3.h)]  
  
 A continuación, la función de `OnDraw` puede ser reescrita como sigue:  
  
 [!code-cpp[NVC_MFC_AxOpt#18](../mfc/codesnippet/CPP/optimizing-control-drawing_4.cpp)]  
  
 Este método evita la creación del lápiz y de pincel cada vez que se llama a `OnDraw` .  La mejora de la velocidad procede a costa de mantener datos adicionales de la instancia.  
  
 Si los cambios de ForeColor o la propiedad BackColor, el lápiz o el pincel necesita crearse de nuevo.  Para ello, reemplace [OnForeColorChanged](../Topic/COleControl::OnForeColorChanged.md) y el miembro de [OnBackColorChanged](../Topic/COleControl::OnBackColorChanged.md) funciona:  
  
 [!code-cpp[NVC_MFC_AxOpt#19](../mfc/codesnippet/CPP/optimizing-control-drawing_5.cpp)]  
  
 Finalmente, eliminar las llamadas innecesarias de `SelectObject` , modifique `OnDraw` como sigue:  
  
 [!code-cpp[NVC_MFC_AxOpt#20](../mfc/codesnippet/CPP/optimizing-control-drawing_6.cpp)]  
  
## Vea también  
 [Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)   
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Asistente para controles ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)   
 [Controles ActiveX MFC: Pintar un control ActiveX](../mfc/mfc-activex-controls-painting-an-activex-control.md)