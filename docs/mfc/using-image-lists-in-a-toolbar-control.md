---
title: "Usar listas de im&#225;genes en un control de barra de herramientas | Microsoft Docs"
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
  - "CToolBarCtrl (clase), listas de imágenes"
  - "listas de imágenes [C++], controles de barra de herramientas"
  - "controles de barra de herramientas [MFC], imagen"
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar listas de im&#225;genes en un control de barra de herramientas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

De forma predeterminada, las imágenes utilizadas por los botones en un control toolbar se almacenan como un mapa de bits.  Sin embargo, también puede almacenar las imágenes de botón en un conjunto de listas de imágenes.  El objeto de control toolbar puede utilizar hasta tres listas independientes de la imagen:  
  
-   La imagen habilitado muestra las imágenes Contains para los botones de la barra de herramientas que se permiten actualmente.  
  
-   La imagen deshabilitado muestra las imágenes Contains para los botones de la barra de herramientas que están deshabilitadas.  
  
-   La imagen resaltado muestra las imágenes Contains para los botones de la barra de herramientas que se resaltan actualmente.  Se utiliza esta lista de imágenes sólo cuando la barra de herramientas utiliza el estilo de **TBSTYLE\_FLAT** .  
  
 Estas listas de imágenes son utilizadas por el control de barra de herramientas cuando se asocian con el objeto de `CToolBarCtrl` .  Creando realiza a esta asociación llamadas a [CToolBarCtrl::SetImageList](../Topic/CToolBarCtrl::SetImageList.md), a [SetDisabledImageList](../Topic/CToolBarCtrl::SetDisabledImageList.md), y a [SetHotImageList](../Topic/CToolBarCtrl::SetHotImageList.md).  
  
 De forma predeterminada, MFC usa la clase de `CToolBar` para implementar las barras de herramientas de la aplicación MFC.  Sin embargo, la función miembro de `GetToolBarCtrl` se puede utilizar para recuperar el objeto incrustado de `CToolBarCtrl` .  Puede hacer llamadas a las funciones miembro de `CToolBarCtrl` mediante el objeto devuelto.  
  
 El ejemplo siguiente muestra esta técnica asignando una imagen habilitado \(`m_ToolBarImages`\) y deshabilitado \(de`m_ToolBarDisabledImages`\) orden a un objeto de `CToolBarCtrl` \(`m_ToolBarCtrl`\).  
  
 [!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/CPP/using-image-lists-in-a-toolbar-control_1.cpp)]  
  
> [!NOTE]
>  Las listas de imágenes utilizadas por el objeto de la barra de herramientas deben ser objetos permanentes.  Por esta razón, son normalmente miembros de datos de una clase MFC; en este ejemplo, la clase de ventana de marco principal.  
  
 Una vez que las listas de imágenes están asociados al objeto de `CToolBarCtrl` , el marco muestra automáticamente el botón correspondiente.  
  
## Vea también  
 [Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)