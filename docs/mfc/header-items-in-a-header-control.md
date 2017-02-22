---
title: "Elementos de encabezado en un control de encabezado | Microsoft Docs"
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
  - "CHeaderCtrl (clase), elementos de encabezado en"
  - "controles [MFC], encabezado"
  - "controles del encabezado, elementos de encabezado en"
  - "elementos de encabezado en controles de encabezado"
ms.assetid: ac79ef1f-a671-4ab2-93e9-b1aa016a48bf
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Elementos de encabezado en un control de encabezado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Tiene control considerable del aspecto y el comportamiento de los elementos de encabezado que forman un control de encabezado \([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)\).  Cada elemento de encabezado puede tener una cadena, una imagen de mapa de bits, una imagen de una lista asociada de la imagen, o un valor de 32 bits definidos por la aplicación asociada al.  La cadena, el mapa de bits, o la imagen se muestra en el elemento de encabezado.  
  
 Puede personalizar el aspecto y el contenido de nuevos elementos cuando se crea mediante una llamada [CHeaderCtrl::InsertItem](../Topic/CHeaderCtrl::InsertItem.md) o modifica un elemento existente, con una llamada a [CHeaderCtrl::GetItem](../Topic/CHeaderCtrl::GetItem.md) y a [CHeaderCtrl::SetItem](../Topic/CHeaderCtrl::SetItem.md).  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Personalizar la apariencia del elemento de encabezado](../mfc/customizing-the-header-item-s-appearance.md)  
  
-   [Ordenar elementos en el control de encabezado](../mfc/ordering-items-in-the-header-control.md)  
  
-   [Proporcionar compatibilidad de arrastrar y colocar para los elementos de encabezado](../mfc/providing-drag-and-drop-support-for-header-items.md)  
  
-   [Utilizando listas de imágenes con los controles de encabezado](../mfc/using-image-lists-with-header-controls.md)  
  
## Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)