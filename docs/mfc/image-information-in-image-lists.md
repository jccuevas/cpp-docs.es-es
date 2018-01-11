---
title: "Información de listas de imágenes de la imagen | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 33248c1bbc225d8d1ccf55c126d1657d0b0e4cad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="image-information-in-image-lists"></a>Información de imágenes en las listas de imágenes
[CImageList](../mfc/reference/cimagelist-class.md) incluye una serie de funciones que recuperen información de una lista de imágenes. El [función miembro GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo) función miembro se llena un `IMAGEINFO` estructura con información acerca de una sola imagen, incluyendo los identificadores de los mapas de imagen y la máscara de bits, el número de planos de color y bits por píxel y el rectángulo delimitador de la imagen en el mapa de bits de la imagen. Puede utilizar esta información para manipular directamente los mapas de bits de la imagen.  
  
 El [función miembro GetImageCount](../mfc/reference/cimagelist-class.md#getimagecount) función miembro recupera el número de imágenes en una lista de imágenes.  
  
 Puede crear un icono basándose en una imagen y una máscara en una lista de imágenes mediante la [función miembro ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon) función miembro. La función devuelve el identificador del nuevo icono.  
  
## <a name="see-also"></a>Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)

