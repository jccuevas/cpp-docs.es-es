---
title: "Informaci&#243;n general sobre los estados de los elementos de control de &#225;rbol | Microsoft Docs"
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
  - "CTreeCtrl (clase), estados del elemento"
  - "estados, CTreeCtrl (elementos)"
  - "controles de árbol, información general de los estados del elemento"
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Informaci&#243;n general sobre los estados de los elementos de control de &#225;rbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada elemento del control de árbol \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) tiene un estado actual.  Por ejemplo, un elemento se puede seleccionar, deshabilitado, expandido, etc.  En general, el control de árbol establece automáticamente el estado de un elemento para reflejar las acciones del usuario, como la selección de un elemento.  Sin embargo, también puede establecer el estado de un elemento utilizando la función miembro de [SetItemState](../Topic/CTreeCtrl::SetItemState.md) y recuperar el estado actual de un elemento utilizando la función miembro de [GetItemState](../Topic/CTreeCtrl::GetItemState.md) .  Para obtener una lista completa de los estados de elemento, vea [Constantes del control de vista de árbol](http://msdn.microsoft.com/library/windows/desktop/bb759985) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
 El parámetro de `nState` especifica el estado actual de un elemento.  Un control de árbol puede cambiar el estado de un elemento para reflejar una acción del usuario, como selección de elementos o establecer el foco al elemento.  Además, una aplicación puede cambiar el estado de un elemento para deshabilitar u ocultar el elemento o para especificar una imagen de grafía o to imagen.  
  
 Cuando se especifica o cambia el estado de un elemento, el parámetro de `nStateMask` especifica que indica los bits para establecer, y el parámetro de `nState` contiene los nuevos valores para esos bits.  Por ejemplo, el ejemplo siguiente se cambia el estado actual de un elemento primario \(especificado por `hParentItem`\) en un objeto de `CTreeCtrl` \(`m_treeCtrl`\) a **TVIS\_EXPANDPARTIAL**:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/CPP/tree-control-item-states-overview_1.cpp)]  
  
 Otro ejemplo de cambiar el estado sería establecer la imagen de baraja de un elemento.  Para ello, `nStateMask` debe incluir el valor de `TVIS_OVERLAYMASK` , y `nState` debe incluir el índice de base uno de la imagen de grafía desplazados a la izquierda ocho bits mediante la macro de [INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) .  El índice puede ser 0 para no especificar ninguna imagen de superposición.  La imagen de mayúsculas y minúsculas se debe agregar a la lista de control del árbol de imágenes de grafía por una llamada anterior a la función de [CImageList::SetOverlayImage](../Topic/CImageList::SetOverlayImage.md) .  La función especifica el índice de base uno de la imagen para agregar; éste es el índice utilizado con la macro de **INDEXTOOVERLAYMASK** .  Un control de árbol puede tener hasta cuatro imágenes sobrepuestas.  
  
 Para establecer la imagen del estado de un elemento, `nStateMask` debe incluir el valor de `TVIS_STATEIMAGEMASK` , y `nState` debe incluir el índice de base uno de la imagen del estado se desplaza a la izquierda 12 bits mediante la macro de [INDEXTOSTATEIMAGEMASK](http://msdn.microsoft.com/library/windows/desktop/bb775597) .  El índice puede ser 0 para no especificar ninguna imagen de estado.  Para obtener más información acerca de las imágenes de superposición y estado, vea [Listas de imágenes del control de árbol](../mfc/tree-control-image-lists.md).  
  
## Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)