---
title: "Usar una lista de im&#225;genes con un control Rebar | Microsoft Docs"
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
  - "listas de imágenes [C++], controles rebar"
  - "controles rebar, listas de imágenes"
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar una lista de im&#225;genes con un control Rebar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada banda rebar puede contener, entre otras cosas, una imagen de una lista asociada de la imagen.  El procedimiento siguiente detalla los pasos necesarios para mostrar una imagen en una banda rebar.  
  
### Para mostrar imágenes en una banda rebar  
  
1.  Asociar una lista de imágenes en el objeto de control rebar mediante una llamada a [SetImageList](../Topic/CReBarCtrl::SetImageList.md), pasando un puntero a una lista existente de la imagen.  
  
2.  Modificar la estructura de **REBARBANDINFO** para asignar una imagen a una banda rebar:  
  
    -   Establezca el miembro de **fMask** a **RBBIM\_IMAGE**, utilizando el OR bit a bit el operador para incluir las marcas adicionales según sea necesario.  
  
    -   Establezca el miembro de `iImage` en el índice de la lista de imágenes de la imagen que se va a mostrar.  
  
3.  Inicializa los miembros de datos restante, como el tamaño, el texto, y el identificador de ventana secundaria contenida, con la información necesaria.  
  
4.  Inserte la nueva banda \(con la imagen\) con una llamada a [CReBarCtrl::InsertBand](../Topic/CReBarCtrl::InsertBand.md), pasando la estructura de **REBARBANDINFO** .  
  
 El ejemplo siguiente se supone que un objeto existente de la lista de imágenes con dos imágenes se asociado al objeto de control rebar \(`m_wndReBar`\).  Una nueva banda rebar \(definida por `rbi`\), que contiene la primera imagen, se agrega con una llamada a `InsertBand`:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/CPP/using-an-image-list-with-a-rebar-control_1.cpp)]  
  
## Vea también  
 [Usar CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Controles](../mfc/controls-mfc.md)