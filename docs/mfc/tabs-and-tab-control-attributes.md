---
title: "Pesta&#241;as y atributos del control de pesta&#241;a | Microsoft Docs"
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
  - "atributos [C++], temas de referencia"
  - "CTabCtrl (clase), atributos de control de pestaña"
  - "controles de fichas, atributos"
  - "pestañas"
  - "pestañas, atributos"
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Pesta&#241;as y atributos del control de pesta&#241;a
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Tiene control considerable del aspecto y el comportamiento de las pestañas que constituyen un control de ficha \([CTabCtrl](../mfc/reference/ctabctrl-class.md)\).  Cada ficha puede tener una etiqueta, un icono, estado de elementos, y un valor de 32 bits definidos por la aplicación asociada a él.  Para cada ficha, puede mostrar el icono, la etiqueta, o ambas.  
  
 Además, cada elemento de ficha puede tener tres estados posibles: presionado, sin prensar, ni resaltado.  Este estado sólo puede establecerse modificando un elemento de tabulación existente.  Para modificar un elemento de tabulación existente, recuperelo con una llamada a [GetItem](../Topic/CTabCtrl::GetItem.md), modificar la estructura de `TCITEM` \(específicamente los miembros de datos de **dwState** y de **dwStateMask** \), y después devuelve la estructura modificada de `TCITEM` con una llamada a [SetItem](../Topic/CTabCtrl::SetItem.md).  Si necesita borrar los estados del elemento de todos los elementos de pestaña en un objeto de `CTabCtrl` , haga una llamada a [DeselectAll](../Topic/CTabCtrl::DeselectAll.md).  Esta función restablece el estado de todos los elementos de pestaña o todos los elementos a menos que el seleccionado actualmente.  
  
 El siguiente código borra el estado de todos los elementos de ficha y modifique el estado del tercer elemento:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/CPP/tabs-and-tab-control-attributes_1.cpp)]  
  
 Para obtener más información sobre los atributos de la pestaña, vea [Fichas y atributos tab.](http://msdn.microsoft.com/library/windows/desktop/bb760550) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  Para obtener más información sobre las fichas a un control de ficha, vea [Fichas a un Control tab](../mfc/adding-tabs-to-a-tab-control.md) más adelante en este tema.  
  
## Vea también  
 [Usar CTabCtrl](../mfc/using-ctabctrl.md)   
 [Controles](../mfc/controls-mfc.md)