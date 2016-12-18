---
title: "Agregar elementos al control | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "CListCtrl (clase), agregar elementos"
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar elementos al control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para agregar elementos al control de lista \([CListCtrl](../mfc/reference/clistctrl-class.md)\), llame a una de varias versiones de la función miembro de [InsertItem](../Topic/CListCtrl::InsertItem.md) , dependiendo de qué información se tiene.  Una versión toma una estructura de [LV\_ITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760) preparar.  Dado que la estructura de `LV_ITEM` contiene miembros numerosos, tiene un mayor control sobre los atributos del elemento del control de lista.  
  
 Dos miembros importantes \(con respecto a la vista de informe\) de la estructura de `LV_ITEM` son miembros de `iItem` y de `iSubItem` .  El miembro de `iItem` es el índice cero\- basado en elemento que la estructura hace referencia y el miembro de `iSubItem` es el índice de base uno de un subelemento, o cero si la estructura contiene información sobre un elemento.  Con estos dos miembros se determina, por cada elemento, el tipo y el valor de la información del subelemento que se muestra cuando el control de lista está en la vista de informe.  Para obtener más información, vea [CListCtrl::SetItem](../Topic/CListCtrl::SetItem.md).  
  
 Los miembros adicionales especifica el texto del elemento, el icono, estado, y los datos de elemento. “Datos de elemento” es un valor definido por la aplicación asociada a un elemento de vista de lista.  Para obtener más información sobre la estructura de `LV_ITEM` , vea [CListCtrl::GetItem](../Topic/CListCtrl::GetItem.md).  
  
 Otras versiones de `InsertItem` utilizan uno o más valores independientes, correspondiente a los miembros de la estructura de `LV_ITEM` , lo inicializar sólo esos miembros que desea usar.  Normalmente, el control de lista administra el almacenamiento para los elementos de lista, pero puede almacenar parte de la información de la aplicación en su lugar, utilizando “elementos de devolución de llamada”. Para obtener más información, vea [Elementos y el De Callback de devolución de llamada](../mfc/callback-items-and-the-callback-mask.md) en este tema y [Elementos y el De Callback de devolución de llamada](http://msdn.microsoft.com/library/windows/desktop/bb774736) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
 Para obtener más información, vea [Elementos y subelementos de vista de lista de la suma](http://msdn.microsoft.com/library/windows/desktop/bb774736).  
  
## Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)