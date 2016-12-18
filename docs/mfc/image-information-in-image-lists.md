---
title: "Informaci&#243;n de im&#225;genes en las listas de im&#225;genes | Microsoft Docs"
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
  - "CImageList (clase), información de imagen en"
  - "listas de imágenes [C++], información de imagen en"
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Informaci&#243;n de im&#225;genes en las listas de im&#225;genes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CImageList](../mfc/reference/cimagelist-class.md) incluye varias funciones que recuperan la información de una lista de imágenes.  La función miembro de [GetImageInfo](../Topic/CImageList::GetImageInfo.md) rellena una estructura de `IMAGEINFO` con información sobre una imagen única, incluidos los identificadores de los mapas de bits de la imagen y la máscara, el número de aviones de color y de bits por píxel, y del rectángulo delimitador de la imagen dentro del mapa de bits de la imagen.  Puede utilizar esta información para manipular directamente los mapas de bits para la imagen.  
  
 La función miembro de [GetImageCount](../Topic/CImageList::GetImageCount.md) recupera el número de imágenes en una lista de imágenes.  
  
 Puede crear un icono basado en una imagen y una máscara en una lista de imágenes utilizando la función miembro de [ExtractIcon](../Topic/CImageList::ExtractIcon.md) .  La función devuelve el identificador del nuevo icono.  
  
## Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)