---
title: "Proporcionar compatibilidad con arrastrar y colocar para los elementos de encabezado | Microsoft Docs"
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
  - "CHeaderCtrl (clase), compatibilidad con arrastrar y colocar"
  - "HDN_ (notificaciones)"
  - "HDS_DRAGDROP (estilo)"
  - "elementos de encabezado en controles de encabezado"
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proporcionar compatibilidad con arrastrar y colocar para los elementos de encabezado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para proporcionar compatibilidad con arrastrar y colocar para los elementos de encabezado, especifique el estilo de `HDS_DRAGDROP` .  Compatibilidad con arrastrar y colocar para los elementos de encabezado le da la capacidad de reordenar los elementos de encabezado de un control de encabezado.  El comportamiento predeterminado proporciona una imagen semitransparente de arrastre de elemento de encabezado que se está arrastrando y un indicador visual de la nueva posición, si se quita el elemento de encabezado.  
  
 Como con funcionalidad de arrastrar y colocar común, puede extender el comportamiento de arrastrar y colocar predeterminado controlando las notificaciones de **HDN\_BEGINDRAG** y de **HDN\_ENDDRAG** .  También puede personalizar el aspecto de la imagen de arrastre reemplazando la función miembro de [CHeaderCtrl::CreateDragImage](../Topic/CHeaderCtrl::CreateDragImage.md) .  
  
> [!NOTE]
>  Si se proporciona compatibilidad con arrastrar y colocar para un control de encabezado incrustado en un control de lista, vea la sección extendida de estilo del tema de [Cambiar los estilos del control de lista](../mfc/changing-list-control-styles.md) .  
  
## Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)