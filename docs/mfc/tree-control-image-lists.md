---
title: "Listas de im&#225;genes del control de &#225;rbol | Microsoft Docs"
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
  - "CTreeCtrl (clase), listas de imágenes"
  - "imágenes [C++], listas en controles de árbol"
  - "controles de árbol, listas de imágenes"
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Listas de im&#225;genes del control de &#225;rbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada elemento del control de árbol \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) puede tener un par de imágenes trazadas una correspondencia de bits asociadas al.  Las imágenes aparecen en el lado izquierdo de la etiqueta de un elemento.  Se muestra una imagen cuando el elemento está seleccionado, y se muestra otra cuando el elemento no está seleccionado.  Por ejemplo, un elemento puede mostrar una carpeta abiertos cuando se selecciona y una carpeta cierra cuando no está seleccionado.  
  
 Para utilizar imágenes de elemento, debe crear una lista de imágenes construye un objeto de [CImageList](../mfc/reference/cimagelist-class.md) y mediante la función de [CImageList::Create](../Topic/CImageList::Create.md) para crear la lista asociada de la imagen.  A continuación agregue los mapas de bits que desea en la lista, y asociar la lista con el control de árbol mediante la función miembro de [SetImageList](../Topic/CTreeCtrl::SetImageList.md) .  De forma predeterminada, todos los elementos muestran la primera imagen en la lista de imágenes para los estados seleccionados y nonselected.  Puede cambiar el comportamiento predeterminado para un elemento determinado especificando los índices de las imágenes seleccionadas y nonselected al agregar el elemento al control de árbol mediante la función miembro de [InsertItem](../Topic/CTreeCtrl::InsertItem.md) .  Puede cambiar índices después de agregar un elemento utilizando la función miembro de [SetItemImage](../Topic/CTreeCtrl::SetItemImage.md) .  
  
 Las listas de imágenes de un control de árbol también pueden contener imágenes de baraja, que están diseñados para ser sobrepuestas en imágenes del elemento.  Un valor distinto de cero en los bits 8 a 11 del estado de un elemento del control de árbol especifica el índice de base uno de una imagen de grafía \(0 no indica ninguna imagen de grafía\).  Porque se utiliza un bit 4, índice de base uno, imágenes de grafía deben estar entre las 15 primeras imágenes en las listas de imágenes.  Para obtener más información sobre estados del elemento del control de árbol, vea [El elemento del control de árbol indica información general](../mfc/tree-control-item-states-overview.md) anteriormente en este tema.  
  
 Si se especifica una lista de imágenes de estado, un control de árbol reserva espacio a la izquierda del icono de cada elemento de una imagen del estado.  Una aplicación puede utilizar imágenes de estado, como casillas unchecked y desactivada, para indicar a estados definidos por la aplicación del elemento.  Un valor distinto de cero en los bits 12 a 15 especifica el índice de base uno de una imagen de estado \(0 no indica ninguna imagen de estado\).  
  
 Especifica el valor de **I\_IMAGECALLBACK** en lugar del índice de una imagen, se puede retrasar la especificación de la imagen seleccionada o nonselected hasta que el elemento esté a punto de volver a dibujar.  **I\_IMAGECALLBACK** dirige el control de árbol ver la aplicación para el índice enviando el mensaje de notificación de [TVN\_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773518) .  
  
 La función miembro de [GetImageList](../Topic/CTreeCtrl::GetImageList.md) recupera el identificador de la lista de imágenes de un control de árbol.  Esta función es útil si necesita agregar más imágenes a la lista.  Para obtener más información sobre las listas de imágenes, vea [Mediante CImageList](../mfc/using-cimagelist.md), [CImageList](../mfc/reference/cimagelist-class.md) en *la referencia de MFC*, y [Listas de imágenes](http://msdn.microsoft.com/library/windows/desktop/bb761389) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)