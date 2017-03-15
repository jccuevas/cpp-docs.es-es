---
title: "Hojas de propiedades como asistentes | Microsoft Docs"
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
  - "hojas de propiedades, como asistentes"
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Hojas de propiedades como asistentes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una característica clave de una hoja de propiedades del asistente es que la navegación se proporciona los botones Siguiente o end, de reserva, y cancelación en lugar de las fichas.  Necesita llamar a [CPropertySheet::SetWizardMode](../Topic/CPropertySheet::SetWizardMode.md) antes de llamar a [CPropertySheet::DoModal](../Topic/CPropertySheet::DoModal.md) en el objeto de hoja de propiedades para aprovechar esta característica.  
  
 El usuario recibe mismo [CPropertyPage::OnSetActive](../Topic/CPropertyPage::OnSetActive.md) y notificaciones de [CPropertyPage::OnKillActive](../Topic/CPropertyPage::OnKillActive.md) mientras pasa de una página a otra página.  El Siguiente y los botones acabados son mutuamente controles exclusivos; es decir, sólo una de ellas se mostrará al mismo tiempo.  En la primera página, el botón siguiente debe estar habilitado.  Si el usuario está en la última página, el botón de final debe estar habilitado.  Esto no se hace automáticamente el marco de trabajo.  Hay que llamar a [CPropertySheet::SetWizardButton](../Topic/CPropertySheet::SetWizardButtons.md) en la última página para ello.  
  
 Para mostrar todos los botones predeterminados, le presentación de ruido de fondo el botón end y mover el botón siguiente.  A continuación mueva el botón atrás para mantener su posición relativa al botón siguiente.  Para obtener más explicación, busque el artículo Q143210 de KB.  Los artículos de Knowledge Base están disponibles en MSDN Library.  
  
## Ejemplo  
 [!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/CPP/property-sheets-as-wizards_1.cpp)]  
  
## Vea también  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md)