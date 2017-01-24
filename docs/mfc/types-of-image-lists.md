---
title: "Tipos de listas de im&#225;genes | Microsoft Docs"
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
  - "CImageList (clase), tipos"
  - "listas de imágenes [C++], tipos de"
  - "listas [C++], imagen"
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tipos de listas de im&#225;genes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Hay dos tipos de listas de imágenes \([CImageList](../mfc/reference/cimagelist-class.md)\): nonmasked y enmascarado.  Una “image nonmasked lista” consta de un mapa de bits de color que contiene una o varias imágenes.  Una “image enmascarada lista” consta de dos mapas de bits de tamaño igual.  El primero es un mapa de bits de color que contiene imágenes, y el segundo es un mapa de bits monocromo que contiene una serie de máscaras \(una para cada imagen del primer mapa de bits.  
  
 Una de las sobrecargas de función miembro de **crear** toma una marca para indicar si la lista de la imagen se enmascarada. \(Otras sobrecargas crear listas enmascaradas de la imagen\).  
  
 Cuando se dibuja una imagen nonmasked, se copia simplemente en el contexto del dispositivo de destino; es decir, se dibuja sobre el color de fondo existente del contexto del dispositivo.  Cuando se dibuja una imagen enmascarada, los bits de la imagen se combinan con los bits de la máscara, que normalmente las áreas transparentes en el mapa de bits donde el color de fondo del contexto del dispositivo de destino muestra a través de.  Puede especificar varios estilos de dibujo al dibujar una imagen enmascarada.  Por ejemplo, puede especificar que la imagen está interpolada para indicar un objeto seleccionado.  
  
## Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)