---
title: "Usar una lista de im&#225;genes | Microsoft Docs"
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
  - "CImageList (clase), utilizar"
  - "listas de imágenes [C++]"
  - "listas [C++], imagen"
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar una lista de im&#225;genes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El uso típico de una lista de imágenes sigue el modelo siguiente:  
  
-   Crea un objeto de [CImageList](../mfc/reference/cimagelist-class.md) y llame a una de las sobrecargas del rol de [crear](../Topic/CImageList::Create.md) para crear una imagen de lista e para adjuntarla al objeto de `CImageList` .  
  
-   Si no agregó imágenes cuando creó la lista de imágenes, agregue imágenes a la lista de imágenes llamando a la función miembro de [Add](../Topic/CImageList::Add.md) o de [de lectura](../Topic/CImageList::Read.md) .  
  
-   Asociar la lista de imágenes con un control llamando a la función miembro de ese control, o imágenes de dibujo de la imagen se muestran utilizando la función miembro de [Dibujar](../Topic/CImageList::Draw.md) de la lista de imágenes.  
  
-   Quizás permite al usuario arrastre una imagen, con compatibilidad integrada de la lista de imágenes para arrastrar.  
  
> [!NOTE]
>  Si la lista de imágenes se realizó con el operador de **new** , debe destruir el objeto de `CImageList` cuando se hace con ella.  
  
## Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)