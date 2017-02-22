---
title: "Superposiciones de im&#225;genes en las listas de im&#225;genes | Microsoft Docs"
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
  - "CImageList (clase), superposición de imágenes en"
  - "listas de imágenes [C++], superposición de imágenes en"
  - "superposiciones"
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Superposiciones de im&#225;genes en las listas de im&#225;genes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada lista de imágenes \([CImageList](../mfc/reference/cimagelist-class.md)\) incluye una lista de imágenes para utilizar como máscaras de superposición.  Una “máscara de grafía” es una imagen dibujada transparente sobre otra imagen.  Cualquier imagen se puede utilizar como máscara de superposición.  Puede especificar hasta cuatro máscaras sobrepuestas por lista de imágenes.  
  
 Agrega el índice de una imagen a la lista de máscaras de grafía utilizando la función miembro de [SetOverlayImage](../Topic/CImageList::SetOverlayImage.md) , el índice de una imagen, y el índice de una máscara de superposición.  Observe que los índices de las máscaras de grafía están basados en lugar de cero\- basados en.  
  
 Dibuja una máscara de grafía sobre una imagen mediante una llamada a **Dibujar**.  Los parámetros incluyen el índice de la imagen para dibujar y el índice de una máscara de superposición.  Debe utilizar la macro de [INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) para especificar el índice de la máscara de superposición.  También puede especificar una imagen de superposición al llamar a la función miembro de [DrawIndirect](../Topic/CImageList::DrawIndirect.md) .  
  
## Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)