---
title: "Destruir el control de lista | Microsoft Docs"
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
  - "CListCtrl (clase), destruir controles"
  - "controles de lista, destruir"
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Destruir el control de lista
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si se inserta el objeto de [CListCtrl](../mfc/reference/clistctrl-class.md) como miembro de datos de una clase de vista o de cuadro de diálogo, se destruye cuando se destruye al propietario.  Si utiliza [CListView](../mfc/reference/clistview-class.md), el marco destruye el control cuando destruye la vista.  
  
 Si se organiza para algunos de los datos de la lista que se almacenarán en la aplicación en lugar del control de lista, necesitará organizar para la desasignación.  Para obtener más información, vea [Elementos y el De Callback de devolución de llamada](http://msdn.microsoft.com/library/windows/desktop/bb774736) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
 Además, es responsable de desasignar cualquier lista de imágenes que creó y que asociado al objeto de control list.  
  
## Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)