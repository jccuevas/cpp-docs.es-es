---
title: "Control de encabezado y control de lista | Microsoft Docs"
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
  - "CHeaderCtrl (clase), con CListCtrl"
  - "CListCtrl (clase), controles del encabezado"
  - "CListCtrl (clase), con CHeaderCtrl"
  - "controles [MFC], encabezado"
  - "controles del encabezado"
  - "controles del encabezado, controles de lista utilizados con"
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Control de encabezado y control de lista
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En la mayoría de los casos, utilizará el control de encabezado que se incrusta en un objeto de [CListCtrl](../mfc/reference/clistctrl-class.md) o de [CListView](../mfc/reference/clistview-class.md) .  Sin embargo, hay casos donde es deseable un objeto independiente del control de encabezado, por ejemplo los datos de manipulación, organizados en columnas o filas, en [CView](../mfc/reference/cview-class.md)\- objeto derivado.  En estos casos, es necesario un mayor control sobre el aspecto y el comportamiento predeterminado de un control de encabezado incrustado.  
  
 En el caso común que desea un control de encabezado para proporcionar el estándar, el comportamiento predeterminado, se puede utilizar [CListCtrl](../mfc/reference/clistctrl-class.md) o [CListView](../mfc/reference/clistview-class.md) en su lugar.  Utilice `CListCtrl` cuando desee la funcionalidad de un control de encabezado predeterminado, incrustado en un control común de vista de lista.  Utilice [CListView](../mfc/reference/clistview-class.md) cuando desee la funcionalidad de un control de encabezado predeterminado, incrustado en un objeto de vista.  
  
> [!NOTE]
>  Estos controles incluyen un solo control de encabezado integrado si el control de vista de lista se crea utilizando el estilo de `LVS_REPORT` .  
  
 En la mayoría de los casos, la apariencia del control de encabezado incrustado puede modificarse cambiando los estilos del control listview que contiene.  Además, la información sobre el control de encabezado se puede obtener con funciones miembro de control principal de la vista de lista.  Sin embargo, para el control total, y el acceso, los atributos y los estilos del control de encabezado incrustado, se recomienda que un puntero al objeto de control de encabezado se recopilado.  
  
 El objeto incrustado del control de encabezado se puede obtener acceso desde **CListCtrl** o de `CListView` con una llamada a la función miembro de `GetHeaderCtrl` de la clase correspondiente.  El código siguiente describe esto:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/CPP/header-control-and-list-control_1.cpp)]  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Utilizando listas de imágenes con los controles de encabezado](../mfc/using-image-lists-with-header-controls.md)  
  
## Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Controles](../mfc/controls-mfc.md)