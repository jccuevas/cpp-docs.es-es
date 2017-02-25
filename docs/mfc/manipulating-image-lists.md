---
title: "Manipular listas de im&#225;genes | Microsoft Docs"
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
  - "CImageList (clase), manipular"
  - "listas de imágenes [C++], manipular"
  - "listas [C++], imagen"
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Manipular listas de im&#225;genes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La función miembro de [Reemplazar](../Topic/CImageList::Replace.md) reemplaza una imagen en una imagen lista \([CImageList](../mfc/reference/cimagelist-class.md)\) con una nueva imagen.  Esta función también es útil si necesita aumentar dinámicamente el número de imágenes en un objeto de la lista de imágenes.  La función de [SetImageCount](../Topic/CImageList::SetImageCount.md) cambiar dinámicamente el número de imágenes almacenadas en la lista de imágenes.  Si aumenta el tamaño de la imagen, llamada **Reemplazar** para agregar imágenes a las nuevas ranuras de la imagen.  Si reduce el tamaño de la imagen, las imágenes más allá del nuevo tamaño se liberan.  
  
 La función miembro de [Quitar](../Topic/CImageList::Remove.md) quita una imagen de una imagen.  La función miembro de [copiar](../Topic/CImageList::Copy.md) puede copiar o cambiar imágenes dentro de una lista de imágenes.  Esta función permite indica si la imagen de origen se copie el índice de destino o imágenes de origen y de destino deben ser intercambiadas.  
  
 Para crear una nueva lista de imágenes combinando dos listas de imágenes, utilice la sobrecarga adecuada de la función miembro de [crear](../Topic/CImageList::Create.md) .  Esta sobrecarga de **crear** combina la primera imagen de listas existentes de la imagen, almacenando la imagen resultante en un nuevo objeto de la lista de imágenes.  La nueva imagen está creada dibujando la segunda imagen transparente a la primera.  Máscara para la nueva imagen es el resultado de realizar una operación OR lógica de los bits de máscaras para las dos imágenes existentes.  
  
 Se repite esto hasta que todas las imágenes se combinan y se agregan al nuevo objeto de la lista de imágenes.  
  
 Puede escribir información de imagen a un archivo llamando a la función miembro de [Escribir](../Topic/CImageList::Write.md) , y se lee la reproducción llamando a la función miembro de [de lectura](../Topic/CImageList::Read.md) .  
  
 [GetSafeHandle](../Topic/CImageList::GetSafeHandle.md), [Adjuntar](../Topic/CImageList::Attach.md), y las funciones miembro de [Desasociar](../Topic/CImageList::Detach.md) permiten manipular el identificador de la imagen asociada al objeto de `CImageList` , mientras que la función miembro de [DeleteImageList](../Topic/CImageList::DeleteImageList.md) elimina la imagen que aparece sin la destrucción de objetos `CImageList` .  
  
## Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)