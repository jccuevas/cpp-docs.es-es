---
title: "Usar controles deslizantes | Microsoft Docs"
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
  - "CSliderCtrl (clase), utilizar"
  - "controles deslizantes"
  - "controles deslizantes, utilizar"
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar controles deslizantes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El uso típico de un control deslizante sigue el modelo siguiente:  
  
-   Se crea el control.  Si el control se especifica en una plantilla de cuadro de diálogo, la creación es automática cuando se crea el cuadro de diálogo. \(Debe tener un miembro de [CSliderCtrl](../mfc/reference/csliderctrl-class.md) en la clase de diálogo correspondiente al control deslizante.\) Alternativamente, puede utilizar la función miembro de [crear](../Topic/CSliderCtrl::Create.md) para crear el control como una ventana secundaria de cualquier ventana.  
  
-   Llame a las distintas funciones específicas de miembro para establecer los valores del control.  Cambios que puede realizar incluyen que establece las posiciones límite del control deslizante, marcas de graduación, de establecer un intervalo de selección, y colocando el control deslizante de nuevo.  Para los controles de un cuadro de diálogo, un buen momento para ello es la función de [OnInitDialog](../Topic/CDialog::OnInitDialog.md) de diálogo.  
  
-   Cuando el usuario interactúa con el control, enviará distintos mensajes de notificación.  Puede extraer el valor del control deslizante de control llamando a la función miembro de [GetPos](../Topic/CSliderCtrl::GetPos.md) .  
  
-   Cuando se hace con el control, debe asegurarse de que se ha destruido correctamente.  Si el control deslizante está en un cuadro de diálogo, éste y el objeto de `CSliderCtrl` se destruyeron automáticamente.  Si no, deberá asegurarse de que el control y el objeto de `CSliderCtrl` están destruirse correctamente.  
  
## Vea también  
 [Usar CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Controles](../mfc/controls-mfc.md)