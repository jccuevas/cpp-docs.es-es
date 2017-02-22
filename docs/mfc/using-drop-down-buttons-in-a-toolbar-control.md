---
title: "Usar botones desplegables en un control de barra de herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TBN_DROPDOWN"
  - "TBSTYLE_EX_DRAWDDARROWS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolBarCtrl (clase), botones desplegables"
  - "botones desplegables en barras de herramientas"
  - "TBN_DROPDOWN (notificación)"
  - "TBSTYLE_EX_DRAWDDARROWS"
  - "barras de herramientas [C++], botones desplegables"
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Usar botones desplegables en un control de barra de herramientas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Además de los botones de comando estándar, una barra de herramientas también puede tener botones desplegables.  Un botón desplegable indica normalmente por la presencia de una flecha abajo asociada.  
  
> [!NOTE]
>  La flecha abajo asociada sólo aparecerá si extendidas se ha establecido `TBSTYLE_EX_DRAWDDARROWS` estilo.  
  
 Cuando el usuario hace clic en esta flecha \(o el botón propio, si no hay ninguna flecha existe\), un mensaje de notificación de `TBN_DROPDOWN` se envía al elemento primario del control de barra de herramientas.  Puede controlar esta notificación y mostrar un menú emergente; similar al comportamiento de Internet Explorer.  
  
 El procedimiento siguiente muestra cómo implementar un botón de la barra de herramientas desplegable con un menú emergente:  
  
### Para implementar un botón desplegable  
  
1.  Una vez creado el objeto de `CToolBarCtrl` , establezca el estilo de `TBSTYLE_EX_DRAWDDARROWS` , mediante el código siguiente:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/CPP/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]  
  
2.  Establezca el estilo de `TBSTYLE_DROPDOWN` para cualquier botón nuevo \([InsertButton](../Topic/CToolBarCtrl::InsertButton.md) o [AddButtons](../Topic/CToolBarCtrl::AddButtons.md)\) o existente \(de[SetButtonInfo](../Topic/CToolBarCtrl::SetButtonInfo.md)\) que tiene botones desplegables.  El ejemplo siguiente se muestra la modificación de un botón existente en un objeto de `CToolBarCtrl` :  
  
     [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/CPP/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]  
  
3.  Agregue un controlador de `TBN_DROPDOWN` a la clase primaria del objeto de la barra de herramientas.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/CPP/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]  
  
4.  En el nuevo controlador, muestre el menú emergente adecuado.  El código siguiente muestra un método:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/CPP/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]  
  
## Vea también  
 [Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)