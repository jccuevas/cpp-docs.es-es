---
title: "Elementos de lista y listas de im&#225;genes | Microsoft Docs"
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
  - "CImageList (clase), y elementos de lista"
  - "CListCtrl (clase), listas de imágenes"
  - "listas de imágenes [C++], elementos de lista"
  - "elementos de lista, listas de imágenes"
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Elementos de lista y listas de im&#225;genes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un “elemento” en un control de lista \([CListCtrl](../mfc/reference/clistctrl-class.md)\) consta del icono, la etiqueta y, posiblemente otra información \(en “subelementos”\).  
  
 Los iconos de los elementos del control de lista se contienen en listas de imágenes.  Una lista de imágenes contiene iconos del mismo tamaño utilizados en vista de iconos.  Segundo, opcional, lista de imagen contiene versiones más pequeñas de los mismos iconos para utilizarlo en otras vistas del control.  Una tercera lista opcional contiene imágenes de “estado”, como casillas, para la presentación delante de los iconos pequeños en determinadas vistas.  Una cuarta lista opcional contiene imágenes que se muestran en los elementos individuales del encabezado del control de lista.  
  
> [!NOTE]
>  Si un control de vista de lista se crea con el estilo de `LVS_SHAREIMAGELISTS` , debe destruir explícitamente las listas de imágenes cuando dejan en uso.  Especifique este estilo si asigna las mismas listas de imágenes a varios controles de vista de lista; si no, más de un control podría intentar destruir la misma lista de imágenes.  
  
 Para obtener más información sobre los elementos de lista, vea [Listas de imágenes de la vista de lista](http://msdn.microsoft.com/library/windows/desktop/bb774736) y [Elementos y subelementos](http://msdn.microsoft.com/library/windows/desktop/bb774736) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  Vea también la clase [CImageList](../mfc/reference/cimagelist-class.md) en *la referencia de MFC* y [Mediante CImageList](../mfc/using-cimagelist.md) en esta familia de casos.  
  
 Para crear un control de lista, necesita proporcionar listas de imágenes que se utilizarán al insertar nuevos elementos en la lista.  El ejemplo siguiente se muestra este procedimiento, donde es puntero `m_pImagelist` de `CImageList` escrito y `m_listctrl` es un miembro de datos de `CListCtrl` .  
  
 [!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/CPP/list-items-and-image-lists_1.cpp)]  
  
 Sin embargo, si no piensa mostrar iconos en la vista de lista o el control de lista, no necesita listas de imágenes.  
  
## Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)