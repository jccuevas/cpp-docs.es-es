---
title: "Operaciones de arrastrar y colocar del control de &#225;rbol | Microsoft Docs"
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
  - "CTreeCtrl (clase), operaciones de arrastrar y colocar"
  - "arrastrar y colocar, CTreeCtrl"
  - "controles de árbol, operaciones de arrastrar y colocar"
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Operaciones de arrastrar y colocar del control de &#225;rbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un control de árbol \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) envía una notificación cuando el usuario inicia para arrastrar un elemento.  El control envía un mensaje de notificación de [TVN\_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773504) cuando el usuario comienza arrastrando un elemento con el botón primario y un mensaje de notificación de [TVN\_BEGINRDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773509) cuando el usuario comienza arrastrando con el botón secundario.  Puede evitar que un control de árbol envíe estas notificaciones dando al control de árbol el estilo de **TVS\_DISABLEDRAGDROP** .  
  
 Se obtiene una imagen para mostrar durante una operación de arrastre llamando a la función miembro de [CreateDragImage](../Topic/CTreeCtrl::CreateDragImage.md) .  El control de árbol crea un mapa de bits que arrastra basado en la etiqueta del elemento que se arrastra.  El control de árbol crea una lista de imágenes, agrega el mapa de bits a, y devuelve un puntero al objeto de [CImageList](../mfc/reference/cimagelist-class.md) .  
  
 Debe proporcionar código que arrastra realmente el elemento.  Esto implica normalmente el uso de las funciones que arrastre de las funciones de la lista de imágenes y el procesamiento de los mensajes de [WM\_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) y de [WM\_LBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms645608) \(o [WM\_RBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms646243)\) enviados después de iniciarse la operación de arrastrar.  Para obtener más información sobre las funciones de la lista de imágenes, vea [CImageList](../mfc/reference/cimagelist-class.md) en *la referencia de MFC* y [Listas de imágenes](http://msdn.microsoft.com/library/windows/desktop/bb761389) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  Para obtener más información sobre arrastrar un elemento del control de árbol, vea [Arrastrar el elemento de vista de árbol](http://msdn.microsoft.com/library/windows/desktop/bb760017), también en [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)].  
  
 Si los elementos en un control de árbol son ser destinos de una operación de arrastrar y colocar, necesita saber cuándo el cursor está en un elemento de destino.  Puede averiguar llamando a la función miembro de [HitTest](../Topic/CTreeCtrl::HitTest.md) .  Especifica un punto y el entero, o la dirección de una estructura de [TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448) que contiene las coordenadas actuales del cursor.  Cuando finaliza la función, integer o estructura contiene un marcador que indica la ubicación del cursor en relación con el control de árbol.  Si el cursor está sobre un elemento en el control de árbol, la estructura contiene el identificador de elemento también.  
  
 Puede indicar que un elemento es el destino de una operación de arrastrar y colocar llamando a la función miembro de [SetItem](../Topic/CTreeCtrl::SetItem.md) para establecer el estado en el valor de `TVIS_DROPHILITED` .  Un elemento que tiene este estado se dibuja en el estilo usado para indicar un destino de arrastrar y colocar.  
  
## Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)